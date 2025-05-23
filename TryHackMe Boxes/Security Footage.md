Description: "Perform digital forensics on a network capture to recover footage from a camera."
"Someone broke into our office last night, but they destroyed the hard drives with the security footage. Can you recover the footage?"

 In this room, we are tasked to analyse a capture file and retrieve the security footage in it.
 We start the room downloading the task file and opening the pcap file with wireshark. 
 Opening the file we are meet with 1109 packets and only one TCP steam.
 ![[SecF1IMG.png]]

If our task is to retrieve a file in the TCP stream we could try `File > Export Objects` in Wireshark, this function extract objects from capture files if possible, but of course it wouldn't be that simple. 
![[SecF1-5IMG.png]]

Next we use the `Follow TCP Stream` function on Wireshark to look through the stream and see what exactly we are dealing with.

![[SecF2IMG.png]]

Before we continue let's analyse the GET request and response.
In the request we don't get any interesting information other than the `Accept:` header which tell us it accepts images.
In the response we get the `Content-Type` header which contains useful information:
- `multipart`: indicates that the body of the response contains more than one part.
- `x-mixed-replace`: indicates that a new part replaces the previous.
- `boundary=`: indicates the string used to separate a port from the other.

This header information is often used for simple streaming, such as, you guessed it, cameras.

We can select just the traffic from the server and save the data as "Raw" so we can try to retrieve the footage from it![[SecF3IMG.png]]

Even though this is not necessary, I've openned the output file in an hex editor to see if I could find any other information about the file. Using your favorite hex editor, in my case [ImHex](https://imhex.werwolv.net/), we was able to determine how many images were sent and how each image starts.
![[SecF4IMG.png]]
![[SecF5IMG.png]]
We can see 540 "--BoundaryString" were found, which indicates, 540 images.
So it would be very tedious to use a hex editor to get each image and save it.
Other observation we can do, is that each image starts with `JFIF` which we call it the "magic numbers" of a file, that is used to determine the type of the file.

We can make an script to get each image and one to combine it and make it a GIF for us to watch.
First let's get those pictures from the binary dump.
![[SecF6IMG.png]]
In this script we start using the import `re` to match the strings "JFIF" and ¨--BoundaryString", which are the start and end of the image respectively.
I then open the raw data dump, determine the strings, and get the positions of the start of each image.
I iterate over those positions and save the chunk of data from the start position to the end position which is the "--BoundaryString" 
One thing to notice is that the starting position is being subtracted by 6, because the start of each image is not exactly at the "JFIF" but six bytes before. This happens because:
- SOI (Start of Image) marker signature, which starts with FF D8.
- APP0 (Application Segment), the first metadata marker, FF E0.
- APP0 Size, which is also 2 bytes, but it says the metadata size, usually 00 10 (16 bytes).
This took a lot of research.
Now using our first script we get the images and check if it  _finally_ works.
![[SecF7IMG.png]]
![[SecF10IMG.png]]
![[SecF8IMG.png]]Great! I got 540 images of what seems to be an cellphone displaying the flag to complete the room. I could end it here and go image by image and getting each digit and letter to reveal the full flag, but that wouldn't be much fun. 
So let's get to the second script.![[SecF9IMG.png]]
This script starts importing `os` and `PIL`, which will help us iterate through the directory (os) to open each image and append them and save it as a GIF (PIL).
Finally I've got the flag in gif format.
![[output.gif]]

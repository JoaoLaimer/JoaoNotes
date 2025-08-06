--When a program is run in [[Windows]], it stores its information for future use. This information is used to load the program quickly in case of frequent use. This information is stored in prefetch files which are located in the `C:\Windows\Prefetch` directory.
Prefetch files have an extension of `.pf`. They contain the last run times, number of times the application was run, any files and device handles used by the files.
We can use Prefetch Parser (PECmd.exe) from Eric Zimmermans's tools.

Parsing File: `PECmd.exe -f <path-to-Prefetch-files> --csv <path-to-save-csv>`

Parsing Dir: `PECmd.exe -d <path-to-Prefetch-directory> --csv <path-to-save-csv>`
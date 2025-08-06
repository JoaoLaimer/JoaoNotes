MFA adds extra protection to user accounts by requiring you to provide two or more verification factors.
2FA (Two-Factor Authentication) is a subset of MFA.
### Types of Authentication Factors
- **Something You Know**: password, PIN, passphrase.
- **Something You Have**: authentication app, security token, smart card.
- **Something You Are**: biometrics, fingerprints, facil recognition.
- **Somewhere You Are**: IP address, geolocation.
- **Something You Do**: Captcha.
### Kinds of 2FA
#### Time-Based One-Time Passwords (TOTP)
Temporary passwords that cange every 30 seconds or so. Apps like Google Authenticator, Microsoft Authenticator, and Authy use them, making them tough for hackers to intercept or reuse.
#### Push Notifications
Applications like Duo or Google Prompt send a login request straight to your phone. You can approve or deny access directly from your device.
An attack involving push notifications, the MFA fatigue attack, enabled an attacker to compromise the corporate account of an Uber employee. You may visit Uber's official security newsroom, which can be found [here](https://www.uber.com/newsroom/security-update).
#### SMS
The system sends a text message with a one-time code to the use's registered phone number.
#### Hardware Tokens
Devices like YubiKeys generate one-time passcode or use NFC for authentication.They’re great because they don’t need a network or battery, so they work even offline.
### Conditional Access
Used by companies to adjust the authentication requirements based on different contexts. It's like a decision tree that triggers extra security checks depending on certain conditions.
#### Location-Based
If a user logs in from an unfamiliar location, the system could ask for an additional OTP or even biometric verification.
#### Time-Based
If someone tries to access the system after working hours, they might be prompted for an extra layer of security, like an OTP or a security token.
#### Behavioral Analysis
If a user begins to access data they don't usually access at odd hours the system can ask fr additional authentication to confirm it's really them.
#### Device-Specific
In some cases, companies don’t allow employees to use their own devices to access corporate resources. In these situations, the system might block the user after the initial login step if they’re on an unapproved device.

---
title: Infostealers, the Modern, Scary, and Increasingly Common Malware Infection
date: 2025-02-12 12:00:00 -0400 # Feb 12, 2025 | 12PM | UTC-4 (EDT)
categories: [Cybersecurity, Malware]
tags: [infostealers]
---

In today’s digital world, we rely on online accounts and the Internet for everything. But unfortunately, there are these increasingly common programs called infostealers, designed to steal all of the information on your computer. These are different than what a lot of people think of when they hear “malware” or “virus.” This is how viruses have changed over the past 5-10 years:

Old viruses:
-   Sketchy popups across your computer
-   Very slow performance
-   Internet not connecting
-   Apps not opening
-   Files corrupted/missing
-   Computer “going mad” and doing things on its own  

Here's an example of what that might look like:
![Image](/assets/img/2025-02-12-infostealers/old-virus.jpg){: width="720" }
_Image of the infamous WannaCry ransomware (2017)._

New viruses:
-   Hide in the background
-   Unnoticeable — most people who have modern malware on their computers don’t know it
-   Very destructive and have some sort of “remote operation” to send information back to the hacker
-   Sometimes they can even “self-destruct” — the virus will make its way to your computer, collect personal information, send it to the hacker, and then the program will delete itself before you realize anything happened.  

Here's an example of what *that* might look like:
![Image](/assets/img/2025-02-12-infostealers/new-virus.png){: width="720" }
_This is the desktop of a PC infected with an infostealer. Notice that it just looks like a normal Windows 11 desktop._

Note that not all modern malware is like that (there is still “classic malware”) but silent and deadly viruses are becoming increasingly common!

### What are Infostealers?

Infostealers are a type of malware like the “new viruses” explained above. They secretly collect your information on your computer. These are some common things infostealers look for:

-   Login credentials: Usernames and passwords for your email, social media, banking, and other accounts
-   Financial information: Credit card numbers, bank account details
-   Personal data: Social Security numbers, addresses, phone numbers
-   Browser data: History, cookies, autofill information, saved passwords in browser
-   Files and documents: Files stored on your computer (photos, videos, documents, programs, data from programs)

The login credentials and browser data are **especially scary**. This is because of tokens. They are very important and helpful, yet vulnerable to abuse. Tokens are like digital keys. They’re used to verify the identity of a user or application without needing to repeatedly provide sensitive credentials like passwords. Think of them as a temporary password stored in your browser — when you visit a site again, it will send the token and the remote server for the website will see “This token is valid and it belongs to this user… success!” Tokens are the reason that you don’t have to sign into a website every time you open the site or refresh the page. But maybe you’re wondering… “How do you _get_ a token?” When you log in to a website, the remote server generates a token and sends it back to your browser. Your browser stores this token in a cookie. That is the token that your browser now ‘owns’ and sends to the remote server every time your computer makes a request to the server. There are different types of tokens but they are all somewhat the same and for the sake of keeping this article short I won’t get into it all.

Once the infostealer gathers this information from your computer, it sends it back to the attacker remotely. Then they can do whatever they choose with this information. Think of the possibilities of what could happen when a hacker gets this much of your info.

### Common Types of Infostealers

Infostealers are all different and they use different methods to steal your info, but they are all very dangerous! Here are some of the most common types:

-   Keyloggers: These programs record *every single thing that you type*. If you type the word “apple” it will get  **logged** (key**logger**). Think about how this could be used maliciously — if you type a website name and then an email, chances are a password will follow that, and boom. The hacker now has your email and password and the website the credentials are for. Basic keyloggers alone aren’t the most helpful because you don’t know  _where_  the user was typing, but other things can be combined with keyloggers like screen recording or screen readers exporting extra data to a logfile.
-   Token Grabbers/Cookie Grabbers: These steal your cookies and extract tokens (explained above) and the hacker is now able to instantly access any of your accounts. Tokens do expire, but if the infostealer sends the data before you sign in again and get a new token, the hacker will have plenty of time to get in, do “malicious things,” and possibly even change your password to something only they know.
-   Form Grabbers/Intercepters: This infostealer variant intercepts data before it gets sent to the ‘intended location.’ They work similar to keyloggers a lot of times, and are basically the same in a lot of cases: the data you type is logged/intercepted and then ‘forwarded’ back to the ‘intended location’ , like a sign-up form for a website, without you knowing it was intercepted.

### How Infostealers Affect your Security

Infostealers can have very devastating consequences for your accounts and security. Just think about what YOU can do. If you have the permissions to do something bad like sending money to someone else or deleting important files (even though you wouldn’t do that) a hacker with your information from an infostealer  _can and will_  do this sort of stuff.

### How to Protect Yourself

Protecting yourself from infostealers can be tough but with the right security, your computer will be safe. Here are some essential steps:

-   Use strong passwords: Choose random passwords for all of your accounts. Use a password manager (I highly recommend  **Bitwarden**!!) to help you generate and store your passwords securely. Your password should be long and random — it should be unreadable gibberish, not “CuteDog12”.
-   Enable two-factor authentication (2FA): 2FA adds an extra layer of security to your accounts by requiring a second form of verification.
    -   SMS two-factor auth is popular but it is not as secure, since phone numbers are vulnerable to SS7 attacks (SS7 attacks allow attackers to intercept text messages before they get to your phone). If it’s your only option, it’s still MUCH better than no 2FA and I still recommend and use SMS 2FA on a lot of my accounts. Sure, SS7 attacks exist, but they aren't too common since they cost a lot of money.
    -   A more secure method to consider is TOTP, or "Time-based One-Time Password Authentication". It’s simple, super secure, and easy. You might know it as an “authenticator app.” These apps give you one-time codes that last for roughly 30 seconds. It's easy to use authenticator apps — you just scan the QR code that the website gives you, using the authenticator app of your choice to scan it and register a new TOTP token, and then you’ll be up and running with TOTP in no time!

> I recommend using Microsoft Authenticator or Google Authenticator.
{: .prompt-tip}

![Image](/assets/img/2025-02-12-infostealers/google-authenticator.png){: width="240" }
_Image of the "Google Authenticator" app (with some information redacted)_

-   Keep your software updated: Regularly update your operating system, web browser, and other software to patch security vulnerabilities that infostealers can exploit. Updates can be annoying, but you should always do them for the sake of your security.
-   Install antivirus and anti-malware software: Use reputable antivirus and anti-malware software to detect and remove infostealers. No antivirus is perfect, but here are my recommendations:  **Windows Defender**  is the built-in antivirus for Windows and it is very good at protecting against malware. And, it’s 100% free and preinstalled.  **Malwarebytes**  doesn’t offer real-time protection unless you pay, but the free version is quite good at detecting malware if you remember to scan periodically.  **Bitdefender**  has a free tier with real-time protection and is another great option if you don’t like Windows Defender, but it can be heavier on your system and is more prone to false positives (antivirus saying something is malware when it is not).  **Kaspersky**  is another great antivirus according to the internet, but it is banned in the US and I haven’t tried it so I can't speak from personal experience.  **Another important note:** Antivirus software like Norton, Avast, McAfee, Avira, AVG, were popular and very good back in the day ~15 years ago but have slowly gotten worse to the point that it’s much worse at virus protection than just using the free antivirus Windows Defender. YouTuber Chris Titus Tech stated in a video that he would “rather get a virus than use (McAfee or Norton)” because of how much they slow down your system and how inaccurate they are when it comes to detecting real threats. They are still better than no antivirus, but considering that Windows has a free, built-in antivirus that is extremely good, I would not recommend using these, it’s pointless.

> For antiviruses, I recommend Windows Defender (built into Windows 10 and 11), or Bitdefender. Malwarebytes is also pretty good. 
{: .prompt-tip}

### How to scan your computer for infostealers

The best AVs (antiviruses) will be able to detect most infostealers, but there is always the risk that you have an undetected infostealer even if you are using the best antivirus. If your antivirus uses real-time behavioral detection, it has a higher chance of detecting even the "undetectable ones".

> **Real-time behavioral detection** is an alternative to **signature-based detection** (which scans your PC and checks if your files are known malware or not) that uses a file's behavior to catch a virus. Programs that have this will be running in the background, monitoring the behavior of files for anything suspicious, such as uploading your files to a server or grabbing cookies from a browser. This method results in more false positives, but is also incredibly good at catching real threats, so for most people the pros outweigh the cons.
{: .prompt-info}

The only 100% reliable way to remove any possible infostealers is to reinstall Windows. This might sound scary and it might be difficult for non-tech-savvy computer users, but it’s not too hard and there are a lot of good guides on the Internet and on YouTube for how to reinstall Windows.

> Make sure to back up all of your important files, since reinstalling Windows will wipe your hard drive.
{: .prompt-warning}

> **Do not "Repair" or "Reset" Windows** - this will keep your files, which sounds convenient, but if there is malware on your computer, it won't be removed.
{: .prompt-info}

If you think you have an infostealer or an antivirus says you have one, and you don’t want to reinstall Windows to remove it, you can try to use the built-in “delete” or “quarantine” function of your antivirus — chances are it will probably work but reinstalling Windows is always the safest option.

By taking these precautions, you can significantly reduce your risk of becoming a victim of infostealers!

Thanks for reading! Don’t forget to follow!

  
Search

[

Write



](https://medium.com/new-story?source=---two_column_layout_nav----------------------------------)

[

](https://medium.com/me/notifications?source=---two_column_layout_nav----------------------------------)

![dollarboysushil](https://miro.medium.com/v2/resize:fill:32:32/0*a-i0o9y-CcVEsnZK)

# TryHackMe: Blue CTF Writeup

[

![dollarboysushil](https://miro.medium.com/v2/da:true/resize:fill:44:44/0*a-i0o9y-CcVEsnZK)









](https://dollarboysushil.medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

[dollarboysushil](https://dollarboysushil.medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

5 min read

·

Just now

[

](https://medium.com/plans?dimension=post_audio_button&postId=6eb0fe0e26bf&source=upgrade_membership---post_audio_button----------------------------------)

![](https://miro.medium.com/v2/resize:fit:700/1*nq8BRQtL0PR4KclIp7dThw.png)

> **This room is not meant to be a boot2root CTF, rather, this is an educational series for complete beginners. Professionals will likely get very little out of this room beyond basic practice as the process here is meant to be beginner-focused.**

Link to lab: [https://tryhackme.com/room/blue](https://tryhackme.com/room/blue)

> For any correction / query /suggestion contact on  
> **Instagram** [dollarboysushil](https://instagram.com/dollarboysushil)  
> **Twitter (X)** [dollarboysushil](https://twitter.com/dollarboysushil)  
> **Youtube** [dollarboysushil](https://youtube.com/dollarboysushil)

# Task 1 : Recon

# Questions.

**Scan the machine. (If you are unsure how to tackle this, I recommend checking out the** [**Nmap**](https://tryhackme.com/room/furthernmap) **room)**

`nmap -sC -sV {IP}` to scan for the ports sunning in the machine.  
here `-sC` runs default scripts  
and `-sV` runs version detections.  
also you can add `-oN` flag to output the result in a file

![](https://miro.medium.com/v2/resize:fit:700/1*oYUhOkHV56EweKhJhzCeGQ.png)

nmap result.

> **How many ports are open with a port number under 1000?  
> Ans: 3**

**What is this machine vulnerable to? (Answer in the form of: ms??-???, ex: ms08–067)**

> **Ans:** _ms17–010 ._

Searching `Windows 7 Professional 7601 Service Pack 1 microsoft-ds` on google shows that the machine is vulnerable to `iternalblue` or `ms17–010`

# Task 2 : Gain Access

**Start** [**Metasploit**](https://tryhackme.com/module/metasploit)

**Find the exploitation code we will run against the machine. What is the full path of the code? (Ex: exploit/……..)**

> Ans : _exploit/windows/smb/ms17_010_eternalblue_

![](https://miro.medium.com/v2/resize:fit:700/1*a0CcuyeT6-rH0VqA6M10AQ.png)

Run metsploit `msfconsole`  
search for eternal blue `search eternal blue`  
From the available list use `exploit/windows/smb/ms17_010_eternalblue`

## Show options and set the one required value. What is the name of this value? (All caps for submission)

> Ans: RHOSTS

use cmd `show options` to list all the available options for the selected modules. And we can see the only empty required field is `RHOSTS` which is the required answer

![](https://miro.medium.com/v2/resize:fit:700/1*y3LjmxhmW80iiQ5umoaCew.png)

![](https://miro.medium.com/v2/resize:fit:559/1*kTybeXULIq7GS2vyqmdSQw.png)

Then set the RHOSTS using `set RHOSTS {IP}` .  
make sure LHOSTS is set as your ip

> RHOST refers to the IP address of the target host  
> LHOST refers to the IP of your machine

## Usually it would be fine to run this exploit as is; however, for the sake of learning, you should do one more thing before exploiting the target. Enter the following command and press enter:

> No answer needed.

## With that done, run the exploit!

> No answer needed.  
> enter `run` to run the exploit

## Confirm that the exploit has run correctly. You may have to press enter for the DOS shell to appear. Background this shell (CTRL + Z). If this failed, you may have to reboot the target VM. Try running it again before a reboot of the target.

> No answer needed

![](https://miro.medium.com/v2/resize:fit:700/1*gVDBfKWUlGmcd9AvX1dy6g.png)

We got shell

# Task 3: Escalate

## If you haven’t already, background the previously gained shell (CTRL + Z). Research online how to convert a shell to meterpreter shell in metasploit. What is the name of the post module we will use? (Exact path, similar to the exploit we previously selected)

> Ans: post/multi/manage/shell_to_meterpreter

Background the shell using `CTRL + Z`

![](https://miro.medium.com/v2/resize:fit:700/1*FXt2flxyoEJvMzkr8Riq_g.png)

## Select this (use MODULE_PATH). Show options, what option are we required to change?

> Ans : Session

![](https://miro.medium.com/v2/resize:fit:700/1*l5EW15YAtvU7bkAoazRAgw.png)

## Set the required option, you may need to list all of the sessions to find your target here.

> No answer needed

![](https://miro.medium.com/v2/resize:fit:700/1*hK_-5ynWkkFYqlOLZiTXHg.png)

Then run the exploit.

If this doesn’t work, try completing the exploit from the previous task once more.

# Task 4 : Cracking

## Within our elevated meterpreter shell, run the command ‘hashdump’. This will dump all of the passwords on the machine as long as we have the correct privileges to do so. What is the name of the non-default user?

> Ans : Jon

![](https://miro.medium.com/v2/resize:fit:620/1*PxXxFHNogkTYUGmX4NPJow.png)

## Copy this password hash to a file and research how to crack it. What is the cracked password?

> Ans: alqfma22

![](https://miro.medium.com/v2/resize:fit:700/1*f6aEo59pAZmCDUt0yLlQug.png)

# Task 5: Finding Flags!

## Flag1? _This flag can be found at the system root._

> Ans: bored to type……

enter cmd `shell`

![](https://miro.medium.com/v2/resize:fit:491/1*S8kQkfw-9JzIqv7vSWEiuw.png)

![](https://miro.medium.com/v2/resize:fit:481/1*rbXTS2EyxMTnkG5VyVDZFg.png)

## Flag2? _This flag can be found at the location where passwords are stored within Windows._

> Ans: bored to type……

![](https://miro.medium.com/v2/resize:fit:411/1*3FjDKzVhmPv8JSYvOHdFZA.png)

## Flag3? _This flag can be found in an excellent location to loot. After all, Administrators usually have pretty interesting things saved._

> Ans: bored to type……

![](https://miro.medium.com/v2/resize:fit:700/1*Bdy1Dxe8zpvGcKPcquKMUw.png)

For this ; go to `C:` and search for file with name flag with command `dir /s flag*.txt`

> For any correction / query /suggestion contact on  
> **Instagram** [dollarboysushil](https://instagram.com/dollarboysushil)  
> **Twitter (X)** [dollarboysushil](https://twitter.com/dollarboysushil)  
> **Youtube** [dollarboysushil](https://youtube.com/dollarboysushil)

[

Tryhackme Walkthrough

](https://medium.com/tag/tryhackme-walkthrough?source=post_page-----6eb0fe0e26bf---------------tryhackme_walkthrough-----------------)

[

Iternal Blue

](https://medium.com/tag/iternal-blue?source=post_page-----6eb0fe0e26bf---------------iternal_blue-----------------)

[

Oscp

](https://medium.com/tag/oscp?source=post_page-----6eb0fe0e26bf---------------oscp-----------------)

[

Cybersecurity

](https://medium.com/tag/cybersecurity?source=post_page-----6eb0fe0e26bf---------------cybersecurity-----------------)

[

Ethical Hacking

](https://medium.com/tag/ethical-hacking?source=post_page-----6eb0fe0e26bf---------------ethical_hacking-----------------)

[

![dollarboysushil](https://miro.medium.com/v2/da:true/resize:fill:72:72/0*a-i0o9y-CcVEsnZK)





](https://dollarboysushil.medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

[

## Written by dollarboysushil

](https://dollarboysushil.medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

[6 Followers](https://dollarboysushil.medium.com/followers?source=post_page-----6eb0fe0e26bf--------------------------------)

@dollarboysushil on Twitter , Instagram , Github , Linkedin

[

Edit profile

](https://medium.com/me/settings/account?source=post_page-----6eb0fe0e26bf--------------------------------#profileInformation)

## More from dollarboysushil

[

![Authentication Vulnerabilities- Lab #9 Brute-forcing a stay-logged-in cookie](https://miro.medium.com/v2/resize:fit:679/1*eUQOjQu5yTJQCZ8dYTTswg.png)

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-9-brute-forcing-a-stay-logged-in-cookie-dda91125f5f2?source=author_recirc-----6eb0fe0e26bf----0---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![dollarboysushil](https://miro.medium.com/v2/resize:fill:20:20/0*a-i0o9y-CcVEsnZK)



](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----0---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

dollarboysushil

](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----0---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

## Authentication Vulnerabilities- Lab #9 Brute-forcing a stay-logged-in cookie

### For any correction / query /suggestion contact on Instagram dollarboysushil Twitter (X) dollarboysushil Youtube dollarboysushil



](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-9-brute-forcing-a-stay-logged-in-cookie-dda91125f5f2?source=author_recirc-----6eb0fe0e26bf----0---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

4 min read·Nov 14

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-9-brute-forcing-a-stay-logged-in-cookie-dda91125f5f2?source=author_recirc-----6eb0fe0e26bf----0---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

1

[](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-9-brute-forcing-a-stay-logged-in-cookie-dda91125f5f2?responsesOpen=true&sortBy=REVERSE_CHRON&source=author_recirc-----6eb0fe0e26bf----0---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![Authentication Vulnerabilities- Lab #3 Password reset broken logic](https://miro.medium.com/v2/resize:fit:679/1*nmPeSuTzYw9Qc-EgWVMukQ.png)

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-3-password-reset-broken-logic-95bc62a7b92a?source=author_recirc-----6eb0fe0e26bf----1---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![dollarboysushil](https://miro.medium.com/v2/resize:fill:20:20/0*a-i0o9y-CcVEsnZK)



](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----1---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

dollarboysushil

](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----1---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

## Authentication Vulnerabilities- Lab #3 Password reset broken logic

### For any correction / query /suggestion contact on Twitter(X) dollarboysushil My social medial handle Instagram dollarboysushil Twitter (X)…



](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-3-password-reset-broken-logic-95bc62a7b92a?source=author_recirc-----6eb0fe0e26bf----1---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

3 min read·Nov 10

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-3-password-reset-broken-logic-95bc62a7b92a?source=author_recirc-----6eb0fe0e26bf----1---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

3

[](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-3-password-reset-broken-logic-95bc62a7b92a?responsesOpen=true&sortBy=REVERSE_CHRON&source=author_recirc-----6eb0fe0e26bf----1---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![Authentication Vulnerabilities- Lab #2 2FA simple bypass](https://miro.medium.com/v2/resize:fit:679/1*SbRqh5wJfxsPtJeLktkoJA.png)

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-2-2fa-simple-bypass-6bd390cf92bc?source=author_recirc-----6eb0fe0e26bf----2---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![dollarboysushil](https://miro.medium.com/v2/resize:fill:20:20/0*a-i0o9y-CcVEsnZK)



](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----2---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

dollarboysushil

](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----2---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

## Authentication Vulnerabilities- Lab #2 2FA simple bypass

### For any correction / query /suggestion contact on Twitter(X) dollarboysushil My social medial handle Instagram dollarboysushil Twitter (X)…



](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-2-2fa-simple-bypass-6bd390cf92bc?source=author_recirc-----6eb0fe0e26bf----2---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

3 min read·Nov 10

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-2-2fa-simple-bypass-6bd390cf92bc?source=author_recirc-----6eb0fe0e26bf----2---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

3

[](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-2-2fa-simple-bypass-6bd390cf92bc?responsesOpen=true&sortBy=REVERSE_CHRON&source=author_recirc-----6eb0fe0e26bf----2---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![Authentication Vulnerabilities- Lab #1 Username enumeration via different responses](https://miro.medium.com/v2/resize:fit:679/1*E971ZOFvKEOcppLnLh_-Mw.png)

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-1-username-enumeration-via-different-responses-7a2562356741?source=author_recirc-----6eb0fe0e26bf----3---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

![dollarboysushil](https://miro.medium.com/v2/resize:fill:20:20/0*a-i0o9y-CcVEsnZK)



](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----3---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

dollarboysushil

](https://dollarboysushil.medium.com/?source=author_recirc-----6eb0fe0e26bf----3---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

## Authentication Vulnerabilities- Lab #1 Username enumeration via different responses

### For any correction / query /suggestion contact on Twitter(X) dollarboysushil My social medial handle Instagram dollarboysushil Twitter (X)…



](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-1-username-enumeration-via-different-responses-7a2562356741?source=author_recirc-----6eb0fe0e26bf----3---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

3 min read·Nov 10

](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-1-username-enumeration-via-different-responses-7a2562356741?source=author_recirc-----6eb0fe0e26bf----3---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

3

[](https://dollarboysushil.medium.com/authentication-vulnerabilities-lab-1-username-enumeration-via-different-responses-7a2562356741?responsesOpen=true&sortBy=REVERSE_CHRON&source=author_recirc-----6eb0fe0e26bf----3---------------------c84f93eb_981d_4652_a724_4069734a11c9-------)

[

See all from dollarboysushil

](https://dollarboysushil.medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

## Recommended from Medium

[

![TryHackMe | Probe Walkthrough](https://miro.medium.com/v2/resize:fit:679/1*zdRbs1MdUHvB85fPBt9NGg.png)

](https://medium.com/@tr1n1ty8/tryhackme-probe-walkthrough-073531c6954f?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![Trnty](https://miro.medium.com/v2/resize:fill:20:20/1*Fec-k_5XH_CgkPQmHWkt-g.png)



](https://medium.com/@tr1n1ty8?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

Trnty

](https://medium.com/@tr1n1ty8?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

## TryHackMe | Probe Walkthrough

### Use your baseline scanning skills to enumerate a secure network.



](https://medium.com/@tr1n1ty8/tryhackme-probe-walkthrough-073531c6954f?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

·3 min read·Nov 12

](https://medium.com/@tr1n1ty8/tryhackme-probe-walkthrough-073531c6954f?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

14

[](https://medium.com/@tr1n1ty8/tryhackme-probe-walkthrough-073531c6954f?responsesOpen=true&sortBy=REVERSE_CHRON&source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![TryHackMe Walkthrough: Dreaming](https://miro.medium.com/v2/resize:fit:679/1*8w1ejCH_FZAQ9INSG-YbWw.png)

](https://medium.com/@sharibbahmadd/tryhackme-walkthrough-dreaming-8d9c026ca7ee?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![Sharib](https://miro.medium.com/v2/resize:fill:20:20/1*8ktVQ9_77MYUIH76-HJ3Vw.png)



](https://medium.com/@sharibbahmadd?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

Sharib

](https://medium.com/@sharibbahmadd?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

## TryHackMe Walkthrough: Dreaming

### Difficulty:easy



](https://medium.com/@sharibbahmadd/tryhackme-walkthrough-dreaming-8d9c026ca7ee?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

6 min read·5 days ago

](https://medium.com/@sharibbahmadd/tryhackme-walkthrough-dreaming-8d9c026ca7ee?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

1

[](https://medium.com/@sharibbahmadd/tryhackme-walkthrough-dreaming-8d9c026ca7ee?responsesOpen=true&sortBy=REVERSE_CHRON&source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

## Lists

[

![A small family — man, woman, and boy, clink glasses over a restaurant table. They all look relaxed and happy.](https://miro.medium.com/v2/da:true/resize:fill:48:48/0*mJ5-XPhtXLnEXjYO)

![](https://miro.medium.com/v2/resize:fill:48:48/1*oPrzEVtpTh4rCCV-ScE-SA.jpeg)

![](https://miro.medium.com/v2/da:true/resize:fill:48:48/0*tEkIsEhVxZT1XLNG)

## Staff Picks

510 stories·463 saves



](https://medium.com/@MediumStaff/list/staff-picks-c7bc6e1ee00f?source=read_next_recirc-----6eb0fe0e26bf--------------------------------)

[

![](https://miro.medium.com/v2/resize:fill:48:48/1*4zC5ohNcmVDb1NXmzCvmNA.jpeg)

![](https://miro.medium.com/v2/resize:fill:48:48/1*0dul7hn9LeV7U2XLVPvYYw.jpeg)

![](https://miro.medium.com/v2/resize:fill:48:48/1*oO7uwYs0NMWV7B4mUCuoIw.png)

## Stories to Help You Level-Up at Work

19 stories·316 saves



](https://medium.com/@MediumStaff/list/stories-to-help-you-levelup-at-work-faca18b0622f?source=read_next_recirc-----6eb0fe0e26bf--------------------------------)

[

![](https://miro.medium.com/v2/resize:fill:48:48/1*VQhBEVqZRXlxFvFVqyTYVA.jpeg)

![](https://miro.medium.com/v2/resize:fill:48:48/1*XRekBY0_j_KEo2_lK_SrkQ.jpeg)

![](https://miro.medium.com/v2/resize:fill:48:48/1*c2stHqktjG8_XTqkC-bkfw.jpeg)

## Self-Improvement 101

20 stories·930 saves



](https://medium.com/@MediumForTeams/list/selfimprovement-101-3c62b6cb0526?source=read_next_recirc-----6eb0fe0e26bf--------------------------------)

[

![](https://miro.medium.com/v2/resize:fill:48:48/1*HWxGot_WiEOZ0fkB_ee2gg.jpeg)

![](https://miro.medium.com/v2/resize:fill:48:48/1*kAzwx9sMsEYm0bMYDTa-lQ.jpeg)

![](https://miro.medium.com/v2/resize:fill:48:48/1*GGLm6Juo_CxQAKEM-mAWfw.jpeg)

## Productivity 101

20 stories·848 saves



](https://medium.com/@MediumForTeams/list/productivity-101-f09f1aaf38cd?source=read_next_recirc-----6eb0fe0e26bf--------------------------------)

[

![TryHackMe | Recovering Active Directory WriteUp](https://miro.medium.com/v2/resize:fit:679/1*-fAGfmPGanb7NTwE59r7cw.png)

](https://medium.com/@abhishek.rk96/tryhackme-recovering-active-directory-writeup-ca4ae916a159?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![DefenderFela](https://miro.medium.com/v2/resize:fill:20:20/1*8FJM0ZZ1TnrzKcqVKkdzDA.png)



](https://medium.com/@abhishek.rk96?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

DefenderFela

](https://medium.com/@abhishek.rk96?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

## TryHackMe | Recovering Active Directory WriteUp

### Link to room:-https://tryhackme.com/room/recoveringactivedirectory



](https://medium.com/@abhishek.rk96/tryhackme-recovering-active-directory-writeup-ca4ae916a159?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

3 min read·Nov 17

](https://medium.com/@abhishek.rk96/tryhackme-recovering-active-directory-writeup-ca4ae916a159?source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

11

[](https://medium.com/@abhishek.rk96/tryhackme-recovering-active-directory-writeup-ca4ae916a159?responsesOpen=true&sortBy=REVERSE_CHRON&source=read_next_recirc-----6eb0fe0e26bf----0---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![Codify (Easy) CTF — HackTheBox](https://miro.medium.com/v2/resize:fit:679/1*V56ORzVhNb1LVhEfw3EPXw.png)

](https://medium.com/@nachoriva84/codify-easy-ctf-hackthebox-466a012c59ce?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![cyx](https://miro.medium.com/v2/resize:fill:20:20/1*vgCSBNwIhIq3M1bY5qnVGA.png)



](https://medium.com/@nachoriva84?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

cyx

](https://medium.com/@nachoriva84?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

## Codify (Easy) CTF — HackTheBox

### From the NMAP scan, ports 80, 22 and 3000 were discoverable. So I proceeded to go to the website



](https://medium.com/@nachoriva84/codify-easy-ctf-hackthebox-466a012c59ce?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

3 min read·Nov 6

](https://medium.com/@nachoriva84/codify-easy-ctf-hackthebox-466a012c59ce?source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

1

[](https://medium.com/@nachoriva84/codify-easy-ctf-hackthebox-466a012c59ce?responsesOpen=true&sortBy=REVERSE_CHRON&source=read_next_recirc-----6eb0fe0e26bf----1---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![HTB Writeup : Codify](https://miro.medium.com/v2/resize:fit:679/1*ID8L0-CgSOZUUzAX8r0X_Q.png)

](https://medium.com/@sselvakumar2407/htb-writeup-codify-7c9b3c0dfef5?source=read_next_recirc-----6eb0fe0e26bf----2---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![Selvakumar](https://miro.medium.com/v2/resize:fill:20:20/1*AaUKM8ZGBYP2UQflALLyYA.jpeg)



](https://medium.com/@sselvakumar2407?source=read_next_recirc-----6eb0fe0e26bf----2---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

Selvakumar

](https://medium.com/@sselvakumar2407?source=read_next_recirc-----6eb0fe0e26bf----2---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

## HTB Writeup : Codify

### Hello Hackers, In this blog, will see about one of the easy boxes in HTB “Codify”.



](https://medium.com/@sselvakumar2407/htb-writeup-codify-7c9b3c0dfef5?source=read_next_recirc-----6eb0fe0e26bf----2---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

4 min read·Nov 13

](https://medium.com/@sselvakumar2407/htb-writeup-codify-7c9b3c0dfef5?source=read_next_recirc-----6eb0fe0e26bf----2---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[](https://medium.com/@sselvakumar2407/htb-writeup-codify-7c9b3c0dfef5?responsesOpen=true&sortBy=REVERSE_CHRON&source=read_next_recirc-----6eb0fe0e26bf----2---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![How I was able to get account takeover via IDOR form JWT](https://miro.medium.com/v2/resize:fit:679/0*7TPXho_Cmu3mSxpV.png)

](https://homosapienimo.medium.com/how-i-was-able-to-get-account-takeover-via-idor-form-jwt-08f3317b938a?source=read_next_recirc-----6eb0fe0e26bf----3---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

![Homo Sapiens](https://miro.medium.com/v2/resize:fill:20:20/1*Ufb9UKU274r9lG4qz0UILg.jpeg)



](https://homosapienimo.medium.com/?source=read_next_recirc-----6eb0fe0e26bf----3---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

Homo Sapiens

](https://homosapienimo.medium.com/?source=read_next_recirc-----6eb0fe0e26bf----3---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

## How I was able to get account takeover via IDOR form JWT

### Hello guys, today I’m gonna explain how I got IDOR and exploit it to make account takeover.



](https://homosapienimo.medium.com/how-i-was-able-to-get-account-takeover-via-idor-form-jwt-08f3317b938a?source=read_next_recirc-----6eb0fe0e26bf----3---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

8 min read·Nov 17

](https://homosapienimo.medium.com/how-i-was-able-to-get-account-takeover-via-idor-form-jwt-08f3317b938a?source=read_next_recirc-----6eb0fe0e26bf----3---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

194

[

1

](https://homosapienimo.medium.com/how-i-was-able-to-get-account-takeover-via-idor-form-jwt-08f3317b938a?responsesOpen=true&sortBy=REVERSE_CHRON&source=read_next_recirc-----6eb0fe0e26bf----3---------------------ab95a2c3_0408_4576_8c38_d56c89c02fb0-------)

[

See more recommendations

](https://medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Help

](https://help.medium.com/hc/en-us?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Status

](https://medium.statuspage.io/?source=post_page-----6eb0fe0e26bf--------------------------------)

[

About

](https://medium.com/about?autoplay=1&source=post_page-----6eb0fe0e26bf--------------------------------)

[

Careers

](https://medium.com/jobs-at-medium/work-at-medium-959d1a85284e?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Blog

](https://blog.medium.com/?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Privacy

](https://policy.medium.com/medium-privacy-policy-f03bf92035c9?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Terms

](https://policy.medium.com/medium-terms-of-service-9db0094a1e0f?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Text to speech

](https://speechify.com/medium?source=post_page-----6eb0fe0e26bf--------------------------------)

[

Teams

](https://medium.com/business?source=post_page-----6eb0fe0e26bf--------------------------------)
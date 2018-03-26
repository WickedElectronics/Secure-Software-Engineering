# Project 8 - Pentesting Live Targets

Time spent: 8 hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

**Vulnerability #1: Session Hijacking/Fixation:** The blue machine is vulnerable to session hijacking / session fixation.
Open two browsers. On one of them, log in to the staff area. Now, find your phpsessionid (there is a tool at
public/hacktools/change_session_id.php that can give it to you directly, but it is also in the storage / cookies
of your developer tools / view source in your browser). Copy the phpsessionid of the logged in browser. Now, on
the other browser (the 'attacker'), replace the phpsessionid with the one from the logged in browser ('victim').
Now, on the attacker, click the login button and it should automatically log you in.

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/hijacking.gif "Session Hijacking Vulnerability")

**Vulnerability #2: SQL Injection (SQLi):** On the blue machine, go to the "Find a Salesperson" page. Once there, click any of the names. Note that in the URL the individuals are referenced by an ID number. On the backend, these are probably put into a query to the database to retrieve the appropriate data. Thus, changing the ID number and adding the SQLi ' OR SLEEP(5)=0--' will cause the page to not load for five seconds. This proves that this is injectable.

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/SQLi.gif "SQL Injection (SQLi) Vulnerability")

## Green

**Vulnerability #1: Cross-Site Scripting:** Submit feedback on the feedback section and enter this JavaScript to the form in the fields other than the email:
<script>alert('Russell found the XSS!');</script>
Log in and view it in the admin section to run it.

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/xss.gif "Cross-Site Scripting (XSS) Vulnerability")

**Vulnerability #2: Username Enumeration:** On the green site, login attempts with usernames that exist but with incorrect
passwords return bold text. With usernames and passwords that do not exist,
it is not bolded. Using this, we could brute force this login page to find all usernames that exist in the database.

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/username%20enumeration.gif "Username Enumeration Vulnerability")

## Red

**Vulnerability #1: Insecure Direct Object Reference:** On the red machine, go to the "Find a Salesperson" page.
Click on any of them. In the URL, you can see they are being referenced by ID. Change that ID to
10 or 11 to access a page you should not be able to. The other two websites do not allow this.

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/insecure%20direct%20object%20reference.gif "Insecure Direct Object Reference (IDOR) Vulnerability")

**Vulnerability #2: Cross-Site Request Forgery (CSRF):** The red site is vulnerable to CSRF attacks against an admin. Just log in
to the site as an admin, open the specially crafted .html file, and the CSRF attack will change the name of the first person in the User database. In this case, I change it from "Blah" to "Russell". I have also included my crafted .html file [here.](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/csrf.html)

GIF Walkthrough: ![alt text](https://github.com/WickedElectronics/Secure-Software-Engineering/blob/Week-8/csrf.gif "Cross-Site Request Forgery (CSRF) Vulnerability")

## Notes

The SQLi took the most time to find by far. The others were found in a couple of hours, but it took **_SEVERAL_** hours to find the SQLi.


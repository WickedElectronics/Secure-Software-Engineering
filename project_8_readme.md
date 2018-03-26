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

Vulnerability #1: Session Hijacking/Fixation: The blue machine is vulnerable to session hijacking / session fixation.
Open two browsers. On one of them, log in to the staff area. Now, find your phpsessionid (they have a tool at
public/hacktools/change_session_id.php that can give it to you directly, but it is also in the storage / cookies
of your developer tools / view source in your browser). Copy the phpsessionid of the logged in browser. Now, on
the other browser (the 'attacker'), replace the phpsessionid with the one from the logged in browser (victim).
Now, on the attacker, click the login button and it should automatically log you in.

Vulnerability #2: __________________


## Green

Vulnerability #1: Cross-Site Scripting: Submit feedback and give this to the form where possible:
<script>alert('Russell found the XSS!');</script>
View it in the admin section to run it

Vulnerability #2: Username Enumeration: On the green site, login attempts with usernames that exist but with incorrect
passwords return bold text. With usernames and passwords that do not exist,
it is not bolded.

## Red

Vulnerability #1: Insecure Direct Object Reference: On the red machine, go to the "Find a Salesperson" page.
Click on any of them. In the URL, you can see they are being referenced by ID. Change that ID to
10 or 11 to access a page you should not. The other two machines do not allow this.

Vulnerability #2: Cross-Site Request Forgery (CSRF): 


## Notes



# Project 8 - Pentesting Live Targets

Time spent: **3** hours spent in total

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

Vulnerability #1: Session Hijacking/Fixation
- Using the session id or a logged in user, you can gain access to the account. The session id should be timestamped or have some signature that should be verified.

![](https://i.imgur.com/AO1gAv6.gif)

Vulnerability #2: SQL Injection (SQLi)
- By injecting some SQL code into the id query paremeter, we can see that the site is susceptible to SQL Injection. For example: 

- `' OR SLEEP(5)=0--'` causes the webpage to wait 5 secs and then display the user with id 1 by default.

- `5' AND SLEEP(5)=0--'` causes the wbpage to wait 5 secs and then load the user with the specified id, in this case, id=5.


![](https://i.imgur.com/ek7EdgZ.gif)



## Green

Vulnerability #1: Username Enumeration
- If a valid user name is entered but with the wrong password, the error display will be in bold: **“Log in was unsuccessful”**
- If the user name does not exist, the error message will not be bold: “Log in was unsuccessful”

![](https://i.imgur.com/bKJq4je.gif)

Vulnerability #2: Cross-Site Scripting (XSS)
- By submitting javascript code into the feedback section of the Contact Us form, when an administrator views the feedbacks, the stored XSS script will be executed.
- `<script>alert('Gotcha...');</script`

![](https://i.imgur.com/TCyeMeV.gif)


## Red

Vulnerability #1: Insecure Direct Object Reference (IDOR)
- Logged in as an administrative user, you can see the sales people that are not visible to the public. However, by changing the id parameter, you can gain access to this information without being logged in.

![](https://i.imgur.com/1kE2M3Z.gif)

Vulnerability #2: Cross-Site Request Forgery (CSRF)
- You can create an HTML form to edit a salesperson’s personal data, such as their first and last name.

![](https://i.imgur.com/KFhMlEI.gif)

## Bonus Objective 2 (Green)

Vulnerability: Stored XSS Redirect
- As a continuation of the XSS attack performed in the Green section, after the stored XSS is executed and the alert message is displayed, the user is redirected to the specified link.
- `<script type="text/javascript">alert('And it was at this moment you messed up...'); window.location = "https://www.redirectURL.com";</script>`

![](https://i.imgur.com/BGlpFfH.gif)



## Notes

Describe any challenges encountered while doing the work
- I understood the proof of concept of the stored XSS redirect but was not sure of the syntax. I have to read the documentation to find this out. In addition to this, Cross-Site Request Forgery was a bit complicated because once again, I was not familiar with the synthax, but had a general underestanding of what should happend and from there was able to figure it out.


## License

    Copyright [2018] [Dwayne Johnson]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

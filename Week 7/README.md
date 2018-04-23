# Project 7 - WordPress Pentesting

Time spent: 4 hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.5.3
    - Fixed in version: 4.6.1
  - [X] GIF Walkthrough: 
     ![](https://i.imgur.com/bvrj933.gif)
  - [X] Steps to recreate: 
    - Log in as a registered user and create a post. Using the HTML editior, you can inject malicious content into your blog post.
    i.e. `<a href="></a><a title=" onmouseover=alert('Test') "> link</a>`
  - [X] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/changeset/33359)

2. Authenticated Cross-Site Scripting (XSS) via Media File Metadata
  - [X] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.1.1
    - Fixed in version: 4.1.16
  - [X] GIF Walkthrough: 
    ![](https://i.imgur.com/12gKtED.gif)
  - [X] Steps to recreate:
    - Log in as an admin and upload an image. This version of Wordpress fails to sanitize filenames, so malicous javascript can be injected into the filename. In this particular example, once the mouse hovers over the image, an alert message is displayed. 
    i.e. `f_societyHACKED <img src= a onerror=alert('HACKED')>.jpg`
  - [X] Affected source code:
    - [Link 2](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)

3. Wordpress: CVE-2017-9061: Cross-Site Scripting (XSS)
  - [X] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.7.4
    - Fixed in version: 4.7.5
  - [X] GIF Walkthrough: 
  - ![](https://i.imgur.com/LaSg7QU.gif )
  - [X] Steps to recreate: 
    - Create a file that is larger than 2 MB. On a Mac operating system you can use the following command in the terminal: `mkfile -n 3m test.jpg`. This will create a 3 MB file named test.jpg. Rename the file with the intended Javascript code to be presented on error.
    i.e. `Test<img src= a onerror=alert('PAWNED')>.jpg`
  - [X] Affected source code:
    - [Link 4 - Security issue 5](https://wordpress.org/news/2017/05/wordpress-4-7-5/)

4. Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [X] Summary: 
    - Vulnerability types: XSS
    - Tested in version: 4.1.1
    - Fixed in version: 4.1.16
  - [X] GIF Walkthrough: 
    ![](https://i.imgur.com/AC8jSvy.gif)
  - [X] Steps to recreate:
    - Log in as a register user and create a post. Using the HTML editor, embed a YouTube video and inject your Javascript code to have a stored XSS attack.
    i.e. `[embed src='https://www.youtube.com/embed/abcd\x3csvg onload=alert("PAWNED...again")\x3e'][/embed]`
  - [X] Affected source code:
    - [Link 4](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)

5. User Enumeration 
  - [X] Summary: 
    - Vulnerability types: User 
    - Tested in version: 4.1.1
    - Fixed in version: Patched via plugins (Wordfence)
  - [X] GIF Walkthrough: 
    ![](https://i.imgur.com/xXdRmky.gif)
  - [X] Steps to recreate:
    - By entering a valid user name, Wordpress notifies you if the password is incorrect and provides a reset link. A brute force dictionary attack can then be executed to gain access to the targeted account. You can use tools such as WPScan to gain access to the account by using the following commmand:

      `wpscan –url [wordpress url]–wordlist [path to wordlist]–username [username to brute force]–threads [number of threads to use]`

    - You can prevent attackers from using brute force methods by keeping track of their IP addreess and limitting the number of login attempts for an IP address. There are several plug-ins available for WordPress to limit the number login attempts for a specific username and IP, such as Wordfence. The latest WordPress versions have the option to limit login attempts by default.
  - [X] Affected source code:
    - [Link 5](https://www.hackingtutorials.org/web-application-hacking/hack-a-wordpress-website-with-wpscan/) 

## Assets

- Kali Linux
- WPScan

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

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

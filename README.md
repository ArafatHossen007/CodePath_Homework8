# Project 7 - WordPress Pentesting

Time spent: **7** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

### 1. (Required) Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [ ] Summary: XSS vulnerability found in an embed shortcode function. An embed URL is passed to a function called autoembed(). 
        This function contains several regular expressions, and if none of them matches the embed URL it simply returns it. 
        A XSS script can be crafted to bypass the regular expressions to get executed. 
    - Vulnerability types:XSS
    - Tested in version:4.2
    - Fixed in version:4.2 
  - [ ] GIF Walkthrough: <img src="youtube.gif" width="800">
  - [ ] Steps to recreate:
          Create a post using the following script: [embed src='https://youtube.com/embed/12345\x3csvg onload=alert(document.cookie)\x3e'][/embed]
          Users who view the post will have the script executed.
 
  - [ ] Affected source: Autoembed function
    - [Link 1](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/class-wp-embed.php)
### 2. (Required) User Enumeration
  - [ ] Summary: Different messages are shown for invalid usernames and valid usernames with incorrect passwords which can lead to user enumeration.
    - Vulnerability types:User Enumeration
    - Tested in version:4.2
    - Fixed in version: N/A
  - [ ] GIF Walkthrough: <img src="user.gif" width="800">
  - [ ] Steps to recreate: 
    Type in "admin" as username with incorrect password shows password is incorrect.
    Type in "random" as username with incorrect password shows invalid username.

  - [ ] Affected source code:Login function
    - [Link 1](https://core.trac.wordpress.org/browser/tags/4.2/src/wp-login.php)
### 3. (Required)  Legacy Theme Preview Cross-Site Scripting (XSS)
  - [ ] Summary:  XSS vulnerability found in preview theme function where one of the callbacks that it takes as argument filters out onclick handlers. 
                  It is then possible for an attacker to craft a XSS script. 
    - Vulnerability types:XSS
    - Tested in version:4.2
    - Fixed in version: 4.2.4
  - [ ] GIF Walkthrough: <img src="legacy.gif" width="800">
  - [ ] Steps to recreate:Inject the following script in a post comment <a href='/wp-admin/' title="" 
                             style="position:absolute;top:0;left:0;width:100%;height:100%;display:block;" onmouseover=alert(document.cookie)//'>Test</a> 
  - [ ] Affected source code:Preview theme function
    - [Link 1](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/theme.php)

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

## License

    Copyright [yyyy] [name of copyright owner]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


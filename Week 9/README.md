# Project 9 - Honeypot

Time spent: **24** hours spent in total


> Objective: In this assignment, we setup a basic honeypot and demonstrate its effectiveness at detecting and/or collecting data about an attack. Utilizing the opensource Honeynet Management Platform - Modern Honey Network (MHN) -  it demonstrates the following basic principles:

-   Successful configuration and deployment of a network-accessible honeypot server with two primary features:
    -   An attack surface that is vulnerable or exposed in some way to network-based attacks
    -   A network security feature such as an IDS (Intrusion Detection System) configured to detect and log such attacks
-   Illustration of at least one attack against the honeypot that can be detected or logged in a way that captures information about the attack or the attacker


## 24 Hour Analysis

**Sensors:** p0f, snort, dionaea

Verify that sensors are up and running using the following command:
`sudo supervisorctl status`

Within the first 24 hours, I only had the p0f and snort sensors deployed. I logged approximately 2k attacks within the 24 hr period. I then added the dionaea sensor and in less than 2 hrs those attacks nearly doubled.

![](https://i.imgur.com/jIJBPSl.gif)

TOP 5 Attacker IPs
TOP 5 Attacked ports
TOP 5 Honey Pots
TOP 5 Attack Signatures

![](https://i.imgur.com/1UyYTgC.gif)


## Notes

Describe any challenges encountered while doing the work
- I may have mentioned this previosily, but I am a visual learner. Once I can envison what needs to be done I can executely it relatively smoothly, with the right resources. The issue I ran into howver was with the Google Cloud Platform server configuration. Unknowing to me, certain sensors can not be set up simulatneously on the same Honeypot server. At the first pass, after the 30 min initial server setup I was excited to deploy as many sensors as I could, so I installed about 10...nothing worked. I was forced to go through the entire installation process again becasue I thought I did somethnig wrong when certain processes weren't running after executing the `sudo supervisorctl status` command. You definetly do learn from your mistakes, because instead of going through the entire **30 min** setup again, I could have used `sudo supervisorctl start [process_name]` to start the process that wasn't running.


## Resources
-   https://hackmd.io/s/SkWWWHa0W
-   http://bagl.io/sec/2015/09/05/MHN-_Deploying_a_Honeypot_Sensor
-   https://itandsecuritystuffs.wordpress.com/2015/02/03/honeypot-networks/
-   https://github.com/threatstream/mhn/wiki/Running-Multiple-Honeypots-on-the-same-server


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
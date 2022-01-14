<div id="top"></div>

# Scouting P.A.S.S.

#### A scouting system for FIRST FRC competitions developed by [PWNAGE - Team #2451](https://pwnagerobotics.org).

<a href="https://PWNAGERobotics.github.io/ScoutingPASS">Live Demo</a> . <a href="#getting-started">Getting Started</a> . <a href="#faq">FAQ</a>
<h1></h1>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#features">Features</a></li>
    <li><a href="#live-demo">Live Demo</a></li>
    <li><a href="#description">Description</a></li>
    <li><a href="#getting-started">Getting Started</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#faq">FAQ</a></li>
    <li><a href="#things-to-add">Things To Add Someday</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

<div id="features"></div>

# Features:
### **Configurable**
  * A JSON configuration file controls the elements of the game to track.  Create a new configuration file each year for the new game, or tweak it week to week to refine your scouting.  No additional coding needed.
### **Universal**
  * Works on any device that has a web browser that runs JavaScript.  Apple, Android, phones, tablets, laptops, it works on them all.
### **Low/No Bandwidth**
  * Neither WiFi nor Cellular required at event.  The web page can be downloaded before the event and doesn't need to be reloaded.
### **Easy hosting**
  * Self hosting via GitHub. (See directions below)
### **[The Blue Alliance Integration](https://thebluealliance.com)**
  * Pull data for the event from The Blue Alliance.  Team #s, Team Names and Schedules

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="live-demo"></div>

## Live Demo
This repository is hosted on GitHub Pages.  You can view a live version of it here: https://PWNAGERobotics.github.io/ScoutingPASS.  (You can host your ScoutingPASS application on GitHub Pages as well.)

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="description"></div>

## Description:
Scouting PASS is a web page displayed in a browser.  It consists of 5 "swipeable" pages each representing a specific aspect of a FRC match: Pre-Match, Autonomous, Teleop, End Game and Post-Match.  A configuratioin file allows the screens to be easily modified to collect any metrics that are important for your scouting needs.  The scouter can use the "Next" or "Prev" buttons or a swiping motion on touchscreens to move between pages.  A QR code is dynamically generated on the last page.  This QR code can be scanned to transfer the data to your data repository.  The QR code can also be stored for processing later using a screenshot or camera.  Once the data has been transfered, the scout hits the clear button and the form is cleared out and ready for the next match.

Configuration is as easy as creating a JSON file with the fields that your scouting team wants to track.  Some fields are common to all teams and years.  The basic fields are:
* Scouter - who is scouting this robot
* Event - the event that is being scouted
* Level - The level of competition (Qualifications, Semi-Finals, Finals, etc)
* Match - the match number that is being scouted
* Robot - Which robot is being scouted (Red-1, Blue-1, etc.)
* Team # - What team is being scouted

User defined fields can be of several different types:
* Text - A freeform text field
* Number - Like text, but restricted to numbers
* Counter - A counter that can be increased or decreased with a click or touch
* Radio Buttons - A single choice between several options (Ball pick up: ()Ground ()Loading Bay ()Both ()None)
* Checkbox - A single on/off or yes/no check box (Exit Start Line?  []Yes if checked)
* Field Image - Using an image of the field, select positions on the field. (Use to record starting point, or shooting locations)

These should cover most of your scouting team's data collection needs.  PWNAGE's 2020 Infinite Recharge configuration file is included as an example.  The import of the configuration file is in index.html and would need to be updated to import a different configuration file. Only import one configuration file.

Since this is a HTML/JavaScript web page, scouters can use almost any device that has a web broswer.  If the device has a touchscreen the screen can be used to swipe back and forth between pages and interact with the data elements.  The webpage only needs to be loaded once.  Once loaded the functionality and data is stored locally in the webpage and doesn't need to be reloaded.  The QR code generation and clear button only resets the form and does not cause the page to reload.  This means that a cellular or WiFi connection is not needed at the competition as long as the webpage is loaded before the event.

If your team has a The Blue Alliance API access token (See https://www.thebluealliance.com/apidocs) the web page will pull team and schedule information from The Blue Alliance.  Put your access token in the authKey variable in resources/js/TBAInterface.js and when the web page is loaded it will load the data (for the event code in the Event field).  This enables some features on the PreMatch Screen.  With the team information the team name will populate just below the Team # field when the team # field is filled in.  If the schedule information is available when the web page is loaded then when the match and robot fields are populated it will automatically populate the team number and team name for the scouter.  This reduces typo errors when entering the team numbers manually.  (Schedules are usually published before the event a day or two before matches start.  However, it may be delayed for various reasons an may only be published hours or minutes before the start of a competition.)

The QR code can be read by a web camera or hand scanner to import the data into the Excel scouting database.  The hand scanner used reads the QR code and inputs the data as if it is typed in from a keyboard.  Included in this repository is the Excel code to pop up an input window and parse the qr data into a row in Excel. (see the [Excel directory](Excel))

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="getting-started"></div>

## Getting Started:
It's really simple to get started:
* Fork GitHub project (as public if you want to host on GitHub Pages)
* Change configuration file (examples in [2020](2020) or [2022](2022) directories)
  * Update your the competition your attending
  * Change the data elements to capture (if desired)
* Enable GitHub Pages in your repository settings ([GitHub Pages Instructions](https://pages.github.com/))
* Load page via GitHub pages (https://<your_username>.github.io/ScoutingPASS)

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="contributing"></div>

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply [open an issue](https://github.com/PWNAGERobotics/ScoutingPASS/issues/new) if anything is missing or unclear in this
  documentation. to let us know what you'd like changed.

Don't forget to give the project a star!

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="faq"></div>

## Frequently Asked Questions:

<details><summary>Why hardcode and disable the event field?</summary>
<br />
The biggest reason is so it doesn't get changed during the event.  If it's changed and your using the TBA features they will not work correctly.  There is no reason to change it during the event and easy to change for your next event.  One more way to reduce mistakes during the event.
</details>

<details><summary>Why doesn't my configuration file load?</summary>
<br />
JSON is a stickler for commas and brackets.  If you see JSON errors check your JSON for missing or extra commas or brackets when adding or removing elements
</details>

<details><summary>What does P.A.S.S. stand for?</summary>
<br />
PWNAGE Analytical Strategy System
</details>

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="things-to-add"></div>

## Things we might want to add someday:
* Timing Element
* Pit Scouting
* More options for processing the QR code

<p align="right">(<a href="#top">back to top</a>)</p>
<div id="license"></div>

## License
Distributed under the GNU GPL v3.0 License. See `LICENSE` for more information.

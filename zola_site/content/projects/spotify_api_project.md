+++
title = "Spotify API"
date = 2023-03-12

[taxonomies]
categories = ["software"]

[extra]
repo_path = "vanbuncha/spotify_api_project"
+++
# Building a Simple Spotify Player with JavaScript
As a music lover and a web developer, I have always been interested in exploring the Spotify Web API and building a simple web application that can control my music playback on the platform. So, I decided to create a simple Spotify player using JavaScript that allows me to log in to my account, fetch my playlists and songs, and control my music playback from a single interface.

## Getting Started
To build this project, I used the following technologies:

- JavaScript for the frontend code
- HTML and CSS for the UI
- Spotify Web API for accessing the Spotify platform
To start building the application, I first had to create a Spotify Web API client ID and secret key, which I obtained by registering a new app on the Spotify Developer Dashboard. I then used the client ID and secret key in my JavaScript code to authenticate the user and fetch their data from the Spotify platform.

## Building the Application
The first step in building the application was to create a UI that allowed me to log in to my Spotify account and fetch my data from the platform. I used HTML and CSS to create a login form that allowed users to enter their Spotify credentials and authenticate the application.

Once the user was authenticated, I used the Spotify Web API to fetch their playlists and songs from the platform. I then displayed this data on the UI in a user-friendly manner, allowing the user to easily navigate and control their music playback.

To control the music playback, I used the Spotify Web API to play/pause, skip to the next or previous track, and adjust the volume of the playback using JavaScript code.
## An Interesting Quirk
As I was building this Spotify player, I noticed an interesting quirk that I had never encountered before. Whenever I made changes to my script.js or style.css files and tried to refresh my browser, the changes would not take effect. I would refresh the page multiple times and even clear my cache, but the old files would remain the same.

After some investigation, I discovered that this issue was caused by browser caching. Browsers often cache static files like JavaScript and CSS files to improve page loading speed. However, this can also lead to issues when developing, as changes to these files may not be immediately reflected in the browser.

To solve this issue, I found that renaming the file and updating the reference in my HTML file solved the problem. For example, if I made changes to script.js, I would rename the file to something like script-v2.js and update the reference in my HTML file accordingly. This forces the browser to recognize the updated file and load the new version.

While this quirk may have caused some frustration (2hours of pure frustration) during development, it was an interesting discovery that taught me more about how browsers handle static files and caching. It also serves as a reminder to always double-check if changes are being reflected in the browser, and to clear the cache if necessary.

Deployment
After completing the development of my Spotify player using JavaScript, HTML, and CSS, I wanted to deploy it on my website and make it accessible to the public. To do this, I followed these simple steps:

Connect to my web hosting provider and access the file manager for my website.
Delete any existing files in the website directory where I wanted to deploy my application.
SSH into your server and navigate to the directory where you want to deploy your application. Then, run the following commands:
```
sudo rm -rf html/spotify_api_project
sudo git clone https://github.com/vanbuncha/spotify_api_project
sudo mv spotify_api_project/spotify_api_project html
sudo rm -rf spotify_api_project
```
These commands will first delete any existing files in the html/spotify_api_project directory, clone the GitHub repository containing your application, move the cloned repository to the html directory, and then delete the original cloned repository.

Ensure that the file permissions for your application files are set correctly, so that they are readable by the web server.
After completing these steps, your Spotify player will be successfully deployed on your website and will be accessible to the public. Anyone who visits the URL for your website can control their Spotify music playback using the web application, making it a convenient and fun addition to your website.

## Conclusion
Building this simple Spotify player was a fun and rewarding experience. I learned a lot about the Spotify Web API and how to use it to create a seamless music playback experience for the user. If you're interested in building your own music player using JavaScript, I highly recommend exploring the Spotify Web API and experimenting with the various features and functionalities it offers. With a little bit of creativity and some JavaScript skills, you can create a custom music player that's tailored to your personal preferences and music taste.

<a href="https://vanguyen.info/spotify_api_project/">Link to the Spotify API project</a>

# To-Do List

- [ ] Add logout option
- [ ] Fetch info about user
- [ ] Fix Currently playing box
- [ ] Passively check currently playing song


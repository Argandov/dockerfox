# DockerFox

What's this and what's it for?

Mostly for security & Compartmentalization, we can run Firefox itself in a Docker container, and leveraging the Unix' X11 server to spawn FF's GUI and use it as usual. 

Note: This doesn't seem to work anymore. Haven't had time to update

### This Dockerfile

- By default everything will be ran as root, so we create a new user 'user' and then, after updating repositories and installing Firefox, we execute everything as 'user'
- Generate HASH password with command `mkpasswd -p sha-512 admin123`
- (Optionally) Create a bashrc profile and drop it in the docker build folder
- This doesn't work on MacOS

### Running it (Tested on Debian & Ubuntu):

`xhost +`

`docker run -d --name dockerfox dockered_firefox -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix`

### Firefox Hardening:
https://github.com/Argandov/hardening/blob/main/browser/guideline.md


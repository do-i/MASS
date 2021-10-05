# Motion on rpi Model 3 B+

## Source

https://www.circuitbasics.com/how-to-make-a-webcam-server-using-the-raspberry-pi-camera/

## Install OS

### Download

    2021-05-07-raspios-buster-armhf.img

### Create SD card

    sudo ./more_dd.sh /dev/sdx 2021-05-07-raspios-buster-armhf.img

### Boot up rpi

enable SSH service

    sudo raspi-config

Select 3 Interface Options

### Run apt remotely

login via ssh from other computer

    sudo apt update
    sudo apt upgrade

## Install Motion and related packages

    sudo apt install autoconf automake build-essential pkgconf libtool git libzip-dev libjpeg-dev gettext libmicrohttpd-dev libavformat-dev libavcodec-dev libavutil-dev libswscale-dev libavdevice-dev default-libmysqlclient-dev libpq-dev libsqlite3-dev libwebp-dev

    wget https://github.com/Motion-Project/motion/releases/download/release-4.3.2/buster_motion_4.3.2-1_armhf.deb

    sudo dpkg -i buster_motion_4.3.2-1_armhf.deb

### Configure motion

    sudo vi /etc/motion/motion.conf

update the following properties

    daemon off -> daemon on
    stream_localhost on -> stream_localhost off
    picture_output on -> picture_output off
    movie_output on ->movie_output off
    framerate 100 – sets how many frames the camera captures in a second
    width 640 – changes the width
    height 480 – changes the height

### Configure motion default

    sudo vi /etc/default/motion

update the following property

    start_motion_daemon=yes


### (Optional) Start motion service

    sudo service motion start

### Enable camera

enable camera service

    sudo raspi-config

Select 3 Interface Options


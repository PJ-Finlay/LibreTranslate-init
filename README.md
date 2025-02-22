# LibreTranslate-init
Run [LibreTranslate](https://libretranslate.com) on Ubuntu 20.04.

Uses [LibreTranslate WSGI](https://community.libretranslate.com/t/is-wsgi-currently-supported/24/3) with [Gunicorn and Nginx](https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-18-04).

```
# Add libretranslate user
useradd libretranslate
mkdir /home/libretranslate
chown libretranslate:libretranslate /home/libretranslate
usermod -aG sudo libretranslate
su libretranslate

# Add swap space (optional)
sudo fallocate -l 10G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo swapon --show

# Download LibreTranslate-init
git clone https://github.com/libretranslate/LibreTranslate-init.git ~/LibreTranslate-init

# Download dependencies and run LibreTranslate on port 5000
~/LibreTranslate-init/setup.sh

# Run LibreTranslate WSGI with nginx and systemd
~/LibreTranslate-init/run.sh

# Check LibreTranslate status
sudo systemctl status libretranslate

```


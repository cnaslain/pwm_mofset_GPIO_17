# Simple MOFSET solution to have a PWM solution using a standard 2 pins ventilator on a raspberry pi.

This implements Andreas Spiess' article and python code (http://www.sensorsiot.org/variable-speed-cooling-fan-for-raspberry-pi-using-pwm-video138/).
I have simply removed the battery stuffs (unused) and add a systemd service?

##Hardware

Components:
- MOFSET IRLZ44n
- R1 1K ohms
- R2: 470 ohms
- Flyback diode 1N400X
- 5V 2 pins ventilator

##Software

I've just modified the following stuffs on the python script:
- new log file for the data output, so I can read them with a LUA script in Domoticz

I've also added a new simple systemd service.

Setup:
```
cd /home/pi
git clone <THIS REPO> pwm_fan
cd pwm_fan
chmod 755 /home/pi/pwm_fan/pwm_mofset_GPIO_17.service
sudo ln -s /home/pi/pwm_fan/pwm_mofset_GPIO_17.service /etc/systemd/system/pwm_mofset_GPIO_17.service
sudo systemctl daemon-reload
sudo systemctl start pwm_mofset_GPIO_17
sudo systemctl status -a pwm_mofset_GPIO_17
sudo systemctl enable pwm_mofset_GPIO_17
```

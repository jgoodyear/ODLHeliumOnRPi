
 Raspberry Pi Configurations
 ===========================

 To free up more memory I followed instructions found off the web
 for increaseing free memory, swap, and tweaking the CPU.

 My initial Helium testing would routinely end in frozen systems, or
 out of memory - some performance tweaks to the RPi platform helped
 to reduce these occurences.

 Perform these modifications to your RPi at your own risk. These instructions
 are provided as is for helping you to reproduce a Helium on RPi setup.

 Note: Most of these commands require root.

 Enable 256MB swapfile
 ---------------------

 echo "CONF_SWAPSIZE=256" > /etc/dphys-swapfile
 dphys-swapfile setup
 dphys-swapfile swapon

 Confirm swap usage with "free -htl" command.

 Replace OpenSSH wth Dropbear.
 -----------------------------

 apt-get install dropbear openssh-client
 /etc/init.d/ssh stop
 sed -i 's/NO_START=1/NO_START=0/g' /etc/default/dropbear
 /etc/init.d/dropbear start
 update-rc.d ssh disable 

 Overclock CPU, SDRAM, and GPU core without increasing voltage:
 Note: Overclock at your own risk.
 ---------------------------------------------------------------

 echo -e "arm_freq=950\nsdram_freq=500\ncore_freq=450\nforce_turbo=1" >> /boot/config.txt

 Replace Deadline Scheduler with NOOP Scheduler:
 -----------------------------------------------

 sed -i 's/deadline/noop/g' /boot/cmdline.txt

 See https://extremeshok.com/1081/raspberry-pi-raspbian-tuning-optimising-optimizing-for-reduced-memory-usage/
 For more ways to reduce/improve RPi performance.

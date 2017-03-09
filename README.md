## deploy-flaskapp-on-vagrant-via-ansible

Ansible deploys [Flask app](https://github.com/Einsteinish/bogo_random_text_redis) on a Vagrant VM. 
Ansible is used as a provisioner to install and configure the VM. 
Just typing "vagrant up", the app will be running and reachable on 
http port 80 at http://192.168.33.15 and http://devops.bogo.com.

Steps:
  - The provisioner cloned [this github repo](https://github.com/Einsteinish/bogo_random_text_redis) into the VM under `/webapps/bogo`
  - Packages installed : git, python-pip, nginx, gunicorn, flask, and redis.
  - The app code in the repo not touched
  - The app will be automatically restarted if crashes or is killed via upstart.
  - The app maxmimize all of the available CPUs - via 'nproc' command in Vagrantfile.
  - The app's logs are captured to `/var/log/bogo/app.log` with hourly logrotate - /etc/cron.daily/logrotate, /etc/logrotate.d/bogo
  - Timezone set to US EST.

Note:
  - Accessing the app with http://devops.bogo.com requires /etc/hosts setup in hosting machine.

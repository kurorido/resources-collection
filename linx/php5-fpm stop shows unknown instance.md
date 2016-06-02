Ubuntu 14.04 php5-fpm stop shows unknown instance

This is a Ubuntu bug

Solution steps:

1. create a file /etc/init/php5-fpm.override with the single line reload signal USR2 in it.
2. sudo pkill php5-fpm; sudo service php5-fpm start

*Content of ram usage script*

#!/usr/bin/bash

touch /home/vagrant/ramusage_logs/ramlog_file.log

date >> /home/vagrant/ramusage_logs/ramlog_file.log

cat /proc/meminfo >> /home/vagrant/ramusage_logs/ramlog_file.log

echo "---" >> /home/vagrant/ramusage_logs/ramlog_file.log

*Content of email script*

#!/usr/bin/bash

cat ramlog_file.log | mail -s "Ramusage" jamiubusayoahmed@gmail.com

*Cron job*
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command

0 1 * * * bash /home/vagrant/ramusage_logs/ramusage.sh
0 0 * * * bash /home/vagrant/ramusage_logs/mailscript.sh


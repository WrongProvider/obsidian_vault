preconfiguracoes no syslog

/etc/logrotate.d/rsyslog

{
    rotate 7
    daily
    maxsize 1G # add this line
    missingok
    notifempty
    delaycompress
    compress
    postrotate
        /usr/lib/rsyslog/rsyslog-rotate
    endscript
}


setup gvm-kali

sudo apt install gvm

sudo gvm-setup

sudo gvm-check-setup

sudo greenbone-feed-sync --type all

sudo gvm-start

problema de merda sem scans roda isso e pois o feed dnv

gvmd --modify-setting 78eceaec-3385-11ea-b237-28d24461215b --value \`gvmd --get-users --verbose | grep admin | awk '{print $2}'\`

sudo  -u  gvm  greenbone-nvt-sync
# linux-pipes-regex-lab
egrep -v '^#' /etc/services | cut -f1 | egrep -v '^$' | sort -u > uniqueservices.txt

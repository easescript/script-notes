Shell Quoting - to enclose a single quote
I was inspired by "Advanced Bash-Scripting Guide" "5.1. Quoting Variables"

Single quotes (' ') operate similarly to double quotes, but do not permit referencing variables, since the special meaning of $ is turned off. 
Within single quotes, every special character except ' gets interpreted literally. 
Consider single quotes ("full quoting") to be a stricter method of quoting than double quotes ("partial quoting").

Since even the escape character (\) gets a literal interpretation within single quotes, trying to enclose a single quote within single quotes will not yield the expected result.

echo "Why can't I write 's between single quotes"

echo

# The roundabout method.
echo 'Why can'\''t I write '"'"'s between single quotes'
#    |-------|  |----------|   |-----------------------|
# Three single-quoted strings, with escaped and quoted single quotes between.

# This example courtesy of Stéphane Chazelas.
The script below is used to load data from a bash script. You can uncomment some lines to test different approaches.

#!/bin/sh

mysql -hmysql1 -Dmail -e "
LOAD DATA LOCAL INFILE '/tmp/spam.txt'
INTO TABLE score
FIELDS TERMINATED BY ','
#ENCLOSED BY '\'' (Created,Sender,Recipient,mail_id,Hits,size,ESMTP_id,response)
ENCLOSED BY \"'\" (Created,Sender,Recipient,mail_id,Hits,size,ESMTP_id,response)
"

#mysql -hmysql1 -Dmail -e '
#LOAD DATA LOCAL INFILE "/tmp/spam.txt"
#INTO TABLE score
#FIELDS TERMINATED BY ","
#ENCLOSED BY "'\''" (Created,Sender,Recipient,mail_id,Hits,size,ESMTP_id,response)
#'

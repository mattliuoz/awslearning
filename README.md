# awslearning

Commond to extract strings
grep -rnw '/Users/mliu/Downloads/1512357814_3478587.csv' -e 'REMOTE_USER' | sed 's/^.*REMOTE_USER="//' | sed 's/\CERT_SERVER.*//' >1.txt

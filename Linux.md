# awslearning

## Commond to extract strings

- grep certain section from csv  
grep -rnw '/Users/mliu/Downloads/1512357814_3478587.csv' -e 'REMOTE_USER' | sed 's/^.*REMOTE_USER="//' | sed 's/\CERT_SERVER.*//' >1.txt

- curl example   
curl --request GET --url https://apiapi.execute-api.ap-southeast-2.amazonaws.com/dev --anyauth -H “Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6Ik5EWkRNakl5UmpBMk9FWTVPRE5DUWpsQlJqQXhORVUyTkVVNFJr3TURJek16aEJNZyJ9.eyJlbWFpbCI6InNzaGV0dHlAc2Vlay5jb20uYXUiLCJpc3MiOiJodHRwczovL2hpcmVyLm9ubGluZWF1dGguZGV2Lm91dGZyYS54eXovIiwic3ViIjoiYXV0aDB8MjgiLCJhdWQiOiJmMkJMOTh6OGk3SE5WbVVKZjZsOEFkY2Zud3ZkWEVVaCIsImlhdCI6MTUxNDQxNzE5NiwiZXhwIjoxNTE0NDUzMTk2LCJhdF9oYXNoIjoiYjZ5dVVlZXRfaks0SDc2SXN5ZU1LUSIsIm5vbmNlIjoiMUxTSElnd2JpOWpHQy1aQVZ1N2VBVEM2bEpweVVtdUwifQ.XzfRb_bqScmvEZ0JKPyq6iF2vMBvU4MLjy0W_DoKPm0fqUxZwKgF-FOSds9U5mSGJapVH8v1kLWyZcRlXx029eUoS7OwhCIvZuOyF0CooR6f6wAEL9f7F_Yq5sLaTytjFMvv0mmS0cscl2LtLL8CLF0Js1AKhdAy4IZ0BWCtegVxMMRPIpMvMCc_C4_MmBrx-3NTQ95P_EaMFi7PyHmQbF59EcVjLD720sgwIT4aL2OGSZXXEWYH4mDOAC-N6LRQVQo3r0aESOjkP5N-zPiX_ci9HEzKaJOC-anClnE7y8KY4rCTbNxfJJ63TIfwMrB3NUk3hf7ARqRJ_paDv3zYKA”

- rm dir  
rm -rf mydir  

## aws
aws ecr get-login . 

## docker
docker build --build-arg <build-arg=xxxxx> -f <DockerfileName> --rm -t <tag> .  
docker run -i -t <tag name>

## git
- clone with ssh key  

```
gitsshkey="xxxxxxxxxx@"
gitsshkeyP=6 #-->ssh://
gitworkroot="${HOME}/work/"

function gitclone(){
    cd $gitworkroot
    gitsshUri="${1:0:gitsshkeyP}${gitsshkey}${1:gitsshkeyP}"
    echo "git clone ${gitsshUri} $gitworkroot"
    git clone $gitsshUri 
}
```
usage: `gitclone ssh://git-codecommit.ap-southeast-2.amazonaws.com/v1/repos/blah-blah`   
what happend: `git clone ssh://xxxxxxxxxx@git-codecommit.ap-southeast-2.amazonaws.com/v1/repos/blah-blah`  


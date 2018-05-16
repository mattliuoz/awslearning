# awslearning

## Commond to extract strings

- grep certain section from csv  
grep -rnw '/Users/mliu/Downloads/1512357814_3478587.csv' -e 'REMOTE_USER' | sed 's/^.*REMOTE_USER="//' | sed 's/\CERT_SERVER.*//' >1.txt

- grep text b/w marker  
example string in food.txt:  
```{{I}} want to {{eat}} anything that's not {{rice}}```  
expected return:  
```I eat rice```  
script looks like:  
```
fileName="food.txt"

vars=$(echo "$a" | sed -n 's:.*{{\(.*\)}}.*:\1;:p' < $fileName | tr -d '[:space:]')

IFS=';' read -a ARR <<< "$vars"
for i in "${ARR[@]}"; do
    echo $i
done
```


- curl example   
curl --request GET --url https://apiapi.execute-api.ap-southeast-2.amazonaws.com/dev --anyauth -H “Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOddLD720sgwIT4aL2OGSZXXEWYH4mDOAC-N6LRQVQo3r0aESOjkP5N-zPiX_ci9HEzKaJOC-anClnE7y8KY4rCTbNxfJJ63TIfwMrB3NUk3hf7ARqRJ_paDv3zYKA”

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


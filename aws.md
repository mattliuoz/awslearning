# Codecommit
## Using ssh

You will be using this uri to clone  

```git clone ssh://Your-IAM-SSH-Key-ID-Here@git-codecommit.ap-southeast-2.amazonaws.com/v1/repos/Your-Repo-Name-Here```

I’ve made a script to add to bash_profile, so that you don’t have to add ssh key id when you try to clone a repo from code commit. All you need to do is just add following code to bash_profile and get correct value of your iam ssh key id and paste it in.
```
# git clone with ssh
gitsshkey="Your-IAM-SSH-Key-ID-Here@"
gitsshkeyP=6
gitworkroot="${HOME}/work/"

function gitclone(){
    cd $gitworkroot
    gitsshUri="${1:0:gitsshkeyP}${gitsshkey}${1:gitsshkeyP}"
    echo "git clone ${gitsshUri} $gitworkroot"
    git clone $gitsshUri 
}
```

## Using HTTPs

It’s required to setup credential help with codecommit authentication.  
https://docs.aws.amazon.com/codecommit/latest/userguide/setting-up-https-unixes.html#setting-up-https-unixes-credential-helper . 


### Notes for macOS user
Keychain is caching credentials for https access (for codecommit) and aws expires temp credential(which is the one used in code commit) in about 15 mins, so check out potential “fix” from above mentioned link.



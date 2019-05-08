## Azure DevOps

### Pipeline as code
- Yaml  
    - Need to authorize to access resouce, how do automate that?  
    - Want to make sure both UAT and PROD are checked, so two tasks needs to run regardless the previous one has failed  

- Tasks  
    - Tried Azure PS task: No luck, coz Az Moudle can't be loaded  
    - Tried PS task: working, but need to setup credentials, yuk!if we do it wrong  
    - Tried Azure CLI:  
        - Not support PS  
        - Only Support Bat for win, bat is pain to work with.  
        - Thought about python, which both Windows and Linux agent supports, but don't want to learn a new language just for a quick job  
        - Then moved on to Linux, so got sh working(hosted ubuntu)

- dos2unix 
    - first time commit it complains about the unepxected token, so found out the sh file is in win format
    - having trouble to run sh in a windows env and hard to test, so did a lot of failed run on pipeline
- Testing script on windows
    - git bash not the best option, coz can't use az
    - does: nope
    - ubuntu on windows 10: yes!
    - cloudshell: it's really good!
    
### Az Cli commands and tricks
- az login: for cli to login to az
- az account list: get list of subscritions
- az account set: use a subscription
- Get all storage accounts  
```AccountNames="$(az storage account list | jq '.[] | .name' | sed 's/"//g')"```
- Get container name for account  
`ContainerNames="$(az storage container list --account-name $accountName | jq '.[] | .name' | sed 's/"//g')"`
- Get container's accessbility, which can be useful for secOps to check if blob is public  
`PublicAccess="$(az storage container show-permission -n $containerName --account-name $accountName)"`


### Questions
How to properly use server principle with pipeline to give least possible access? 
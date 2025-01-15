#!groovy
// it means the libraries libraries will be downloaded and accessible at run  time
@Library('roboshop-library') _
def configMap = [
    application: "nodeJSEKS"
    component: "catalogue"
]
// this is .groovy filename and function inside it
env
//if not master then trigger pipeline
if(!env.BRANCH_NAME.equalsIgnoreCase('master')){
pipelineDecission.decidePipeline(configMap)
}
else{
    echo "master PROD deployment should happen through CR requests"
}


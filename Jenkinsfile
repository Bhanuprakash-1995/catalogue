#!groovy
@Library('roboshop-shared-library') _

// resposibility to pass what types of application and component is the piplineDesicion

def configMap = [
    application: "nodejsVM",
    component: "catalogue"
]

if( ! env.BRANCH_NAME.equalsIgnoreCase('main')) {
    pipelineDecision.decidePipeline(configMap)
}
else {
    echo "This is production, deal with CR process"
}
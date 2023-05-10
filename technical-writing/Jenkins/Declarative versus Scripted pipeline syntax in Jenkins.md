## Declarative versus Scripted pipeline syntax in Jenkins


A Jenkinsfile can be written using two types of syntax - Declarative and Scripted.

Declarative and Scripted Pipelines are constructed fundamentally differently. Declarative Pipeline is a more recent feature of Jenkins Pipeline which:
* provides richer syntactical features over Scripted Pipeline syntax, and
* is designed to make writing and reading Pipeline code easier.

Many of the individual syntactical components (or "steps") written into a Jenkinsfile, however, are common to both Declarative and Scripted Pipeline. 
Declarative Pipeline fundamentals

**Declarative pipeline syntax**

In Declarative Pipeline syntax, the pipeline block defines all the work done throughout your entire Pipeline.
**Jenkinsfile (Declarative Pipeline)**

    pipeline {
        agent any (1)
          stages {
            stage('Hello') {
                steps {
                    echo 'Hello World'
                }
            }
            stage('Build') {(2)
                steps {
                    echo 'Building'(3)
                }
            }
            stage('Deploy') {(4)
                steps {
                    echo 'Deploying'(5)
                }
            }
            stage('Test') {(6)
                steps {
                    echo 'Testing'(7)
                }
            }
            stage('Release') {(8)
                steps {
                    echo 'Releasing'(9)
                }
            }
        }
        
    }
1. Execute this Pipeline or any of its stages, on any available agent.
2. Defines the "Build" stage.
3. Perform some steps related to the "Build" stage.
4. Defines the "Deploy" stage.
5. Perform some steps related to the "Deploy" stage.
6.Defines the "Test" stage.
7. Perform some steps related to the "Test" stage.
8. Defines the "Release" stage.
9. Performs some steps related to the "Release" stage.

**Scripted Pipeline fundamentals**

In Scripted Pipeline syntax, one or more node blocks do the core work throughout the entire Pipeline. Although this is not a mandatory requirement of Scripted Pipeline syntax, confining your Pipeline’s work inside of a node block does two things:
1. Schedules the steps contained within the block to run by adding an item to the Jenkins queue. As soon as an executor is free on a node, the steps will run.
2. Creates a workspace (a directory specific to that particular Pipeline) where work can be done on files checked out from source control.
**Caution**: Depending on your Jenkins configuration, some workspaces may not get automatically cleaned up after a period of inactivity. 

**Jenkinsfile (Scripted Pipeline)**

    node {(1)
        stage('Build') {(2)
            //(3)
        }
        stage('Test') {(4)
            //(5)
        }
        stage('Deploy') {(6)
            //(7)
        }
    }

1. Execute this Pipeline or any of its stages, on any available agent.
2. Defines the "Build" stage. stage blocks are optional in Scripted Pipeline syntax. However, implementing stage blocks in a Scripted Pipeline provides clearer visualization of each `stage’s subset of tasks/steps in the Jenkins UI.
3. Perform some steps related to the "Build" stage.
4. Defines the "Test" stage.
5. Perform some steps related to the "Test" stage.
6. Defines the "Deploy" stage.
7. Perform some steps related to the "Deploy" stage.


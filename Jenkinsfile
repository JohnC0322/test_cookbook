//This Jenkinsfile is the pipeline of from workstation to "Production". Included checking the linting test, test-kitchen, and integration test.//Afterward, upload the cookbook that are in the master branch to chef-server and supermarket.

pipeline {
    // The running agent is node labled as a "master", in this case, it the master. It can also assign to multiple workers or groups.
    agent { label "master"}
    // environment {
    // EXTRA= "your path needs here"
    //   }
    stages {
        // withEnv(["PATH+EXTRA=$EXTRA"]) { ##this is how you'd add path to this stage
        // sh 'chef shell-init sh' ## this is if chef shell env isn't seeing everything
        // stage('Workstation Verify'){
        // steps {
        //     sh 'echo "Versions: "'
        //     sh 'chef --version'
        //     sh 'cookstyle --version'
        //     sh 'foodcritic --version'
        //     sh 'echo "updating Berkshelf: "'
        //     sh 'if [ ! -f Policyfile.rb]; then chef install Policyfile.rb; else echo nothing; fi;'
        //     }
        // }

        // stage ('Version Check'){
        //     when {
        //         branch 'master'
        //     }
        //     steps {
        //         //Fail when cookbook exists in Chef with same version as code repo. Pass when code version not found in Chef.
        //         sh '''#!/bin/bash
        //         COOKBOOK=$(cat metadata.rb | grep name | awk '{printf $2}' | sed 's/\\x27//g')
        //         export $COOKBOOK
        //         COOKVER=$(cat metadata.rb | grep -e "^version" | awk '{printf $2}' | sed 's/\\x27//g')
        //         if knife cookbook show $COOKBOOK $COOKVER; then false; else true; fi
        //         '''
        //     }
        // }

        stage('Acceptance Testing') {
        steps {
            parallel(
            Cookstyle: {
                sh'echo "Starting cookstyle (rubocop): "'
                sh'cookstlye'
                }
            // FoodCritic: {
            //     sh'echo "Starting foodcritic: "'
            //     sh'foodcritic . --tags -FC078'
            //     },
            // ChefSpec: {
            //     sh'echo Starting ChefSpec: '
            //     sh'chef exec rspec'
            //     }
            )
            }
        }
        
        // Spin up a test infrascture and run test kitchen on it.
        // stage('Test Kitchen') {
        //  steps {
        //      sh 'kitchen test -d always --color'
        //     }
        // }

        // stage('Upload Policy File') {
        //     steps {
        //         sh 'chef push poc Policyfile.rb'
        //     }
        // }

        stage('Upload cookbook to Chef Server & Supermarket') {
            step {
                sh '''#!/bin/bash
                '''
            }
        }

        // stage('Upload Profile to Automate'){
        //     steps{
        //         sh '''#!/bin/bash
        //         COOKBOOK=$(cat metadata.rb | grep name | awk '{printf $2}' | sed 's/\\x27//g')
        //         export $COOKBOOK
        //         COOKVER=$(cat metadata.rb | grep -e "^version" | awk '{printf $2}' | sed 's/\\x27//g')
        //         #if knife cookbook show $COOKBOOK $COOKVER; then false; else true; fi
                
        //         # Check for existing profile
        //         # futher info: https://automate.chef.io/docs/profiles/
        //         # curl --insecure -H "x-data-collector-token: <TOKEN>" <URL> -d
        //         # create tarball
        //         # upload new profile
        //         '''
        //     }
        // }

        // stage('Delete the workspace'){
        //     steps {
        //       sh "rm -rf $WORKSPACE/*"
        //       sh "rm -rf $WORKSPACE/.* | true"
        //     }
        // }
    }
}

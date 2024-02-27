#!/usr/bin/env groovy

pipeline {
    parameters { 
        booleanParam(name: 'SBOM_STUDIO', defaultValue: true, description: 'Enable Cybeats SBOM Studio')
    }
    agent any
    stages {
        stage('Stage 1') {
            steps {
                echo 'Testing Jenkins SBOM Studio Plugin'
                sh 'pwd'
                sh 'ls -al'
            }
        }

        stage('Stage 2') {
            steps {
                echo 'Check General Functionality'
                sbomStudio filePath: 'sboms/arduino-cli.json',
                            manufacturerId: 'Cybeats', 
                            pkgType: '-', 
                            sbomComponentName: '', 
                            sbomComponentNamespace: '', 
                            sbomComponentVersion: '', 
                            subType: 'application', 
                            supplierId: 'Cybeats'
            }
        }

        stage('Stage 3') {
            steps {
                echo 'Check No Parameters'

                try{
                    sbomStudio filePath: 'sboms/arduino-cli.json' //,
                                // manufacturerId: 'Cybeats', 
                                // pkgType: '-', 
                                // sbomComponentName: '', 
                                // sbomComponentNamespace: '', 
                                // sbomComponentVersion: '', 
                                // subType: 'application', 
                                // supplierId: 'Cybeats'
                }catch(err){
                    echo err.getMessage()
                }
            }
        }

        stage('Stage 4') {
            echo 'fourth stage'
        }

        stage('Stage 5'){
            echo 'fifth'
        }
    }
}
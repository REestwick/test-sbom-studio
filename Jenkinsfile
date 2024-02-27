#!/usr/bin/env groovy

pipeline {
    parameters { 
        booleanParam(name: 'SBOM_STUDIO', defaultValue: true, description: 'Enable Cybeats SBOM Studio')
    }
    agent any
    stages {
        stage('Stage 0') {
            steps {
                echo 'Testing Jenkins SBOM Studio Plugin'
                sh 'pwd'
                sh 'ls -al'
            }
        }

        stage('Stage 1') {
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
                sh 'echo $?'
            }
        }

        stage('Stage 2') {
            steps {
                echo 'Check No Parameters'
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS'){   
                    sbomStudio filePath: 'sboms/arduino-cli.json' //,
                                // manufacturerId: 'Cybeats', 
                                // pkgType: '-', 
                                // sbomComponentName: '', 
                                // sbomComponentNamespace: '', 
                                // sbomComponentVersion: '', 
                                // subType: 'application', 
                                // supplierId: 'Cybeats' 
                    sh 'echo $?'  
                }
            }
        }

        stage('Stage 3') {
            steps{
                echo 'Check Full Parameters'
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS'){   
                sbomStudio filePath: 'sboms/arduino-cli.json',
                            manufacturerId: 'Cybeats', 
                            pkgType: 'golang', 
                            sbomComponentName: 'Arduino-CLI-Jenkins', 
                            sbomComponentNamespace: 'com.arduino-cli-jenkins', 
                            sbomComponentVersion: '1.0.0', 
                            subType: 'application', 
                            supplierId: 'Cybeats'
                    sh 'echo $?'   
                }
            }
        }

        stage('Stage 4'){
            steps{
                echo 'Check Invalid manufacturerId'
                sbomStudio filePath: 'sboms/arduino-cli.json',
                            manufacturerId: 'CybeatsNotTheRightInput', 
                            pkgType: '-', 
                            sbomComponentName: '', 
                            sbomComponentNamespace: '', 
                            sbomComponentVersion: '', 
                            subType: 'application', 
                            supplierId: 'Cybeats'
                sh 'echo $?'
            }
        }
    }
}
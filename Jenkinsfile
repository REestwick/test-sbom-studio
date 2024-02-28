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
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
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
        }

        stage('Stage 2') {
            steps {
                echo 'Check No Parameters'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){   
                    sbomStudio filePath: 'sboms/arduino-cli.json'  
                }
            }
        }

        stage('Stage 3') {
            steps{
                echo 'Check Full Parameters'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){   
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'golang', 
                                sbomComponentName: 'Arduino-CLI-Jenkins', 
                                sbomComponentNamespace: 'com.arduino-cli-jenkins', 
                                sbomComponentVersion: '1.0.0', 
                                subType: 'application', 
                                supplierId: 'Cybeats'  
                }
            }
        }

        stage('Stage 4'){
            steps{
                echo 'Check Invalid manufacturerId'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'CybeatsNotTheRightInput', 
                                pkgType: '-', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'   
                }
            }
        }

        stage('Stage 5'){
            steps{
                echo 'Check Invalid supplierId'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '-', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'CybeatsNotTheRightInput'   
                }
            }
        }

        stage('Stage 6') {
            steps {
                echo 'Check Wrong pkgType'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'somepackagetype', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 7') {
            steps {
                echo 'Blank pkgtype'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 8') {
            steps {
                echo 'Whitespace pkgtype'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '   ', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 9') {
            steps {
                echo 'Whitespace sbomComponentName'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '', 
                                sbomComponentName: '    ', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 10') {
            steps {
                echo 'Whitespace sbomComponentNamespace'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '    ', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 11') {
            steps {
                echo 'Whitespace sbomComponentVersion'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '   ', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '    ', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 12') {
            steps {
                echo 'Blank subType'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: '', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 13') {
            steps {
                echo ''
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: '', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 14') {
            steps {
                echo 'Check SBOM No Root Component'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli-no-root.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: '-', 
                                sbomComponentName: '', 
                                sbomComponentNamespace: '', 
                                sbomComponentVersion: '', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }

        stage('Stage 15') {
            steps {
                echo 'Check SBOM No Root Component With Metadata'
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE'){
                    sbomStudio filePath: 'sboms/arduino-cli-no-root.json',
                                manufacturerId: 'Cybeats', 
                                pkgType: 'golang', 
                                sbomComponentName: 'Arduino-CLI-No-Root', 
                                sbomComponentNamespace: 'com.arduino-cli-no-root-jenkins', 
                                sbomComponentVersion: '1.2.3', 
                                subType: 'application', 
                                supplierId: 'Cybeats'
                }
            }
        }
    }
}
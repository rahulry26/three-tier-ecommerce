pipeline {

    options {
                // Timeout counter starts BEFORE agent is allocated
                timeout(time: 1, unit: 'SECONDS')
            }

    stages {
        stage('Build Image') {
            agent any
            
            steps {
                echo 'Find All the Dockerfiles'

                Powershell '''

                    function Imagebuild{
                        
                        param(
                            [string]$dir
                            [string]$imagename
                    )

                        docker build -t $imagename:${env:BUILD_ID} $dir\\.                

                    }

                    Imagebuild -dir ${env:WORKSPACE}\\cart -imagename cart

                '''

            }
        }
    }
}
node {
        stage 'Checkout'
        /* Checkout the code we are currently running against */
            checkout scm

                stage 'Build'
                    /* Build the Docker image with a Dockerfile, tagging it with the build number */
                        def app = docker.build "alpine-test:${env.BUILD_NUMBER}"

        stage 'Push'
        /* Push the Docker image to private registry */
                        docker.withRegistry("https://registryserver:443") {
                        app.push()
        }
        }

pipeline {
    agent any

    stages {
        stage('Back-end') {
            agent {
                docker {
                    image 'openjdk:17'
                }
            }
            steps {
                sh '''
                cat > HelloWorld.java <<EOF
                public class HelloWorld {
                    public static void main(String[] args) {
                        System.out.println("Hello World!");
                    }
                }
                EOF

                javac HelloWorld.java
                java HelloWorld
                '''
            }
        }

        stage('Front-end') {
            agent {
                docker {
                    image 'node:16-alpine'
                }
            }
            steps {
                sh '''
                cat > index.html <<EOF
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Hello</title>
                </head>
                <body>
                    <h1>Hello Adarsh Ji</h1>
                </body>
                </html>
                EOF

                echo "Generated index.html"
                cat index.html
                '''
            }
        }
    }
}

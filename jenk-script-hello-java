pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                script {
                    // Create the directory for the Java program
                    sh 'mkdir -p src/main/java'
                    
                    // Write the HelloWorld.java file
                    writeFile file: 'src/main/java/HelloWorld.java', text: '''\
                    public class HelloWorld {
                        public static void main(String[] args) {
                            System.out.println("Hello, World!");
                        }
                    }
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Create the directory structure for compiled classes
                    sh 'mkdir -p classes'
                    
                    // Compile the Java program
                    sh 'javac -d classes src/main/java/HelloWorld.java'
                }
            }
        }

        stage('Run') {
            steps {
                script {
                    // Run the Java program
                    sh 'java -cp classes HelloWorld'
                }
            }
        }
    }

    post {
        always {
            // Clean up the workspace
            cleanWs()
        }
    }
}

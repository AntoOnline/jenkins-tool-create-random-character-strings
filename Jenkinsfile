pipeline {
    agent any
    parameters {
        string(name: 'username_length', defaultValue: '9', description: 'Length of the generated username')
        string(name: 'password_length', defaultValue: '12', description: 'Length of the generated password')
    }
    stages {
        stage('Generate Usernames and Passwords') {
            steps {
                script {
                    // Generate username
                    def vowels = ['a', 'e', 'i', 'o', 'u']
                    def consonants = ['b', 'c', 'd', 'f', 'g', 'h', 'j', 'k', 'l', 'm', 'n', 'p', 'q', 'r', 's', 't', 'v', 'w', 'x', 'y', 'z']
                    def chars = vowels + consonants
                    def username_length_int = username_length.toInteger()
                    def username = ''
                    for (i in 1..username_length_int) {
                        def random_index = (int) (Math.random() * chars.size())
                        username += chars[random_index]
                        chars = chars.minus(chars[random_index])
                    }

                    // Generate password
                    chars = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z', '!', '#', '$', '%', '&', '*', '+', '-', '.', '/', ':', ';', '<', '=', '>', '?', '@', '^', '_', '{', '|', '}', '~']
                    def password_length_int = password_length.toInteger()
                    def password = ''
                    for (i in 1..password_length_int) {
                        password += chars[(int) (Math.random() * chars.size())]
                    }

                    // Generate password hashes
                    def base64Password = password.bytes.encodeBase64().toString()
                    def sha256Password = java.security.MessageDigest.getInstance("SHA-256").digest(password.getBytes()).encodeHex().toString()
                    def command = "echo -n '${password}' | md5sum | awk '{print \$1}'"
                    def md5Password = sh(script: command, returnStdout: true).trim()

                    echo "Generated username: ${username}"
                    echo "Generated password (alphanumeric): ${password}"
                    echo "Generated password (base64): ${base64Password}"
                    echo "Generated password (SHA-256): ${sha256Password}"
                    echo "Generated password (MD5): ${md5Password}"
                }
            }
        }
    }
}

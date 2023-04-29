# Pipeline for Generating a Random Set of Strings

This pipeline generates a random username and password. The pipeline is written in Groovy and can be run on Jenkins.

## Usage
Clone this repository to your local machine.

Open the Jenkinsfile in your favorite text editor and configure the following parameters:

username_length: the length of the generated username (default: 9).
password_length: the length of the generated password (default: 12).
Create a new Jenkins job and set the pipeline script to the content of Jenkinsfile.

Run the job.

The generated username and passwords will be displayed in the console output of the job.

## How it works

The pipeline generates a random username and password using a set of predefined characters. The username is generated by selecting random consonants and vowels until the desired length is reached. The password is generated by selecting random characters from a set of lowercase and uppercase letters, numbers, and special characters.

Additionally, the pipeline generates the password in base64, SHA-256 formats, etc.

## Want to connect?

Feel free to contact me on [Twitter](https://twitter.com/OnlineAnto) or [LinkedIn](https://www.linkedin.com/in/anto-online) if you have any questions or suggestions.

Or just visit my [website](https://anto.online) to see what I do.

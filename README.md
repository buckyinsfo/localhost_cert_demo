# An Express.js Server Demo w/ localhost HTTPS 

This is an example project demonstrating the setup and procedure for handling HTTPS requests and serving responses in a local development environment.

---
## Setup

## On a windows system 
### Install NodeJS.
    1 Use the chocolatey to install the latest NodeJS version on your local system.
    2 Use the chocolatey to install the latest Git version on your local system.
    2 Checkout this codebase using Git. >git <..path to this github..>
    3 Run >npm install


### Install mkcert
    1 Use the chocolatey to install the latest mkcert (https://github.com/FiloSottile/mkcert)
        - In powershell w/ admin rights run: >choco install mkcert

    2 Create the local CA (Certificate Authority).  This is basically like a localized mini Verisign or LetsEncrypt that only applies to the local machine.
        - In powershell w/ admin rights run: >mkcert -install
        - To verify the location of the CA keys run: >mkcert -CAROOT

    3 Create an environment variable called CAROOT with value of the path returned from >mkcert -CAROOT 

### Generaate the local project cert and key using mkcert
    4 Generate the project certificates.
        - In powershell in the local project top level folder run: 
            >mkdir .ssl
            >cd .ssl
            >mkcert example.com "*.example.com" example.test localhost 127.0.0.1 ::1

        This will output the certificate and key for my project.

    5 Verify the cert and key fies are referenced correctly in the json object passed in at the https server creation.
        - look in ./bin/www around lines 22-36

### Run dev server
- >npm run dev

### In a browser navigate to:
https://localhost:10443

---
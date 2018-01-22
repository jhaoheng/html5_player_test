# about ssl

- If you wnat to use self-signed: 
    1. use `sh ./ssl/generate-CA.sh`
    2. move 'your-computer-name.crt / .csr / .key' to 'server.crt / .csr / .key'
    3. check ssl configure tag are set already in nginx.conf
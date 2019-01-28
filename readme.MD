## This is a gitlab / bitbucket pipeline to convert .md files to .html files.

### Setting up ftp 

To upload files to the ftp server, use the following values

`HOST: "ftp host"`

`USERNAME: "gebruikersnaam"`

`PASSWORD: "Wachtwoord"`

To change the upload location 

- lftp -c  "set ftp:ssl-allow no; open -u $USERNAME,$PASSWORD $HOST; mirror -Rnev ./ `./location`  -e --delete-first --parallel=10 --exclude-glob .git* --exclude .sh --exclude .gitlab-ci.yml --exclude /node_modules/*" 

## This is a gitlab / bitbucket pipeline to convert .md files to .html files.

### Setting up ftp 

To upload files to the ftp server, use the following values. 
For public projects, see [Gitlab documentation](https://docs.gitlab.com/ee/ci/variables/#variables).

`HOST: "your FTP host"`

`USERNAME: "your FTP username"`

`PASSWORD: "your FTP password"`

To change the upload location, simply change the `myfolderlocation`.

lftp -c  "set ftp:ssl-allow no; open -u $USERNAME,$PASSWORD $HOST; mirror -Rnev ./ `./myfolderlocation`  -e --delete-first --parallel=10 --exclude-glob .git* --exclude .sh --exclude .gitlab-ci.yml 
--exclude /node_modules/*" 

How to run ftp protocol
1. unzip ftp.zip to a new folder "unzip_ftp"
2. clone BinPRE: `git clone https://github.com/ecnusse/BinPRE.git`
3. go to BinPRE folder 
4. run `sudo docker build . -t binpre_ae`
5. run `sudo docker run -v /path/to/unzip_ftp:/mnt/ftp -it binpre_ae /bin/bash`

operations in the container
1. build a folder `ftp` under "{BinPRE_home}/src"
2. build a folder 'ftp_50` under "{BinPRE_home}/BinPRE_Res/"
2. cp `fftp` and `fftp.conf` from "unzip_ftp" to the `ftp`
3. cp sh files from "unzip_ftp" to "{BinPRE_home}/Artifact_Evaluation/BinPRE_scripts/"
4. cp `s7.py` and `__init__.py` from "unzip_ftp" to "{BinPRE_home}/Analyzer/Groundtruth"
5. then run "run_ftp_server.sh" in a terminal
6. run `sudo docker container ls -a` to find a container whose image name is `binpre_ae`
7. use "sudo docker exec -it {container_name} /bin/bash" to start a new terminal, where {containter_name} is from 6th step
8. then run "run_ftp_client.sh"

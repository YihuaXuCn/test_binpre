1. clone the repo: `git clone https://github.com/YihuaXuCn/llm_pre.git`
2. clone BinPRE: `git clone https://github.com/ecnusse/BinPRE.git`
3. go to llm_pre and unzip taint.zip to {BinPRE_home}/PUT_test
4. download docker image tar file from https://drive.google.com/file/d/15HBdl8QZHSGurn5QoH0L-222eiS0Ta57/view?usp=sharing 
5. loading image using `sudo docker load -i llm_pre.tar`
6. go out of llm_pre and start a containter using: `sudo docker run -v /path/to/BinPRE_home:/mnt/binpre -v /path/to/llm_pre:/home/linuxbrew/our_sys -v /path/to/folder:/home/linuxbrew/our_output -it llm_pre:yxu131_v1 /bin/bash`
7. run the following command in the container: cd llm_pre && python3 llm_pre.py -a --without-loop  -eval -intra -n 3 --few-shots -p {protocol_name} &> {protocol_name}.txt


How to run ftp protocol
1. unzip ftp.zip to a new folder "unzip_ftp"
2. clone BinPRE: `git clone https://github.com/ecnusse/BinPRE.git`
3. go to BinPRE folder 
4. run `sudo docker build . -t binpre_ae`
5. replace the last instruction to `sudo docker run -v /path/to/ftp:/mnt/ftp -it binpre_ae /bin/bash`

operations in the container
1. build a folder `ftp` under "{BinPRE_home}/src"
2. build a folder 'ftp_50` under "{BinPRE_home}/BinPRE_Res/"
2. cp `fftp` and `fftp.conf` from "unzip_ftp" to the `ftp`
3. cp sh files from "unzip_ftp" to "{BinPRE_home}/Artifact_Evaluation/BinPRE_scripts/"
4. cp `s7.py` and `__init__.py` from "unzip_ftp" to "{BinPRE_home}/Analyzer/Groundtruth"
5. then run "run_ftp_server.sh" in a terminal
6. use "sudo docker exec -it {container_name} /bin/bash" to start a new terminal
7. then run "run_ftp_client.sh"
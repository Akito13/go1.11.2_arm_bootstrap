# Cross-compiling go1.11.2 bootstrap for ARM i.e. Raspberry Pi
#### Follow the instructions exactly step by step to make sure the directories are created as intended. Failing to do so will make everything fail.

1. Install dependencies

    ```bash
    sudo apt install wget git make build-essential
    ```
2. Get go1.4 toolchain bootstrap source code

    ```bash
    mkdir ~/src ; cd ~/src ; mkdir go1.4-bootstrap-20171003 ; cd go1.4-bootstrap-20171003
    wget https://dl.google.com/go/go1.4-bootstrap-20171003.tar.gz
    tar zxvf go1.4-bootstrap-20171003.tar.gz --strip-components 1 && rm go1.4-bootstrap-20171003.tar.gz && cd src
    ```
3. Compile go1.4 toolchain
    ```bash
    CGO_ENABLED=0
    make.bash
    cd ../..
    ```
    
4. Get go1.11.2 for the host system assuming the host system is of the `amd64` architecture
    
    ```bash
    mkdir go1.11.2 ; cd go1.11.2
    wget https://dl.google.com/go/go1.11.2.linux-amd64.tar.gz
    tar zxvf go1.11.2.linux-amd64.tar.gz --strip-components 1 && rm go1.11.2.linux-amd64.tar.gz && cd src
    ```
    
5. Set environment variables and compile go1.11.2 toolchain
    ```bash
    export GOROOT_BOOTSTRAP="/home/akito/src/go1.4-bootstrap-20171003"
    GOOS=linux GOARCH=arm ./bootstrap.bash
    cd ../..
    ```

6. Now you are in ~/src where the directory `go-linux-arm-bootstrap` folder is created, which you need to proceed to the next part. Use the README.md to proceed as needed.

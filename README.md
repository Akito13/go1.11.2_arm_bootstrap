# Bootstrapping go1.11.2 on Raspberry Pi
#### Follow the instructions exactly step by step to make sure the directories are created as intended. Failing to do so will make everything fail.
##### All this must be applied on the target Raspberry Pi system.


-----




0. Install dependencies

    ```bash
    sudo apt install wget git build-essential
    ```

1. Clone the repository and set `GOROOT_BOOTSTRAP` environment variable
   
   
    ```bash
    mkdir ~/src ; cd ~/src ; git clone https://github.com/Akito13/go1.11.2_arm_bootstrap.git
    export GOROOT_BOOTSTRAP=/home/pi/src/go1.11.2_arm_bootstrap/go-linux-arm-bootstrap
    ```
   
   
2. You are in the `~/src` folder now and retrieve the Go source code:

    i.
    ```bash
    mkdir go1.11.2 ; cd go1.11.2
    git clone https://go.googlesource.com/go . && cd src
    ```
    
    ii. Switch to desired version: 
    
    ```bash
    git checkout go1.11.2
    ```

3. You compile the actual Go that Raspberry Pi will use now:
 
    i.   
    ```bash
    ./make.bash
    ```
       
    ii. This will take some time, so be patient.

4. Test your Go installation:
    
    i.
    
    ```bash
    cd .. ; cd bin ; nano hello.go
    ```
    
    ii. You paste in the following:
    
    ```go
    package main

    import "fmt"

    func main() {

            fmt.Printf("GO-reetings!\n")

    }
    ```

    iii. Now do
    
    ```bash
    ./go run hello.go
    ```
    
    and output should be 
    
    ```bash
    GO-reetings!
    ```


5. Set your environment ready to GO:

    ```bash
    export PATH="$PATH:/home/pi/src/go1.11.2/bin" && export GOPATH=$HOME/go
    ```
    
6. Check if PATH is set correctly:
  
    ```bash
    go version
    ```
    
    and output should be
    
    ```bash
    go version go1.11.2 linux/arm
    ```
    
    which means everything is set up correctly!

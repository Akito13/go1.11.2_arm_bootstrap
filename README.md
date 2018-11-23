# Bootstrapping go1.11.2



1. mkdir ~/src ; cd ~/src ; git clone https://git.greenfinch.tk/Akito/go1.11.2_bootstrap.git
2. `export GOROOT_BOOTSTRAP=/home/pi/src/go-linux-arm-bootstrap`
3. You are in the ~/src folder now. Now you get the newest go (using the master branch):
    1. `git clone https://go.googlesource.com/go`
    2. `cd go`
    3. (Optional) You may also switch to go1.11.2 instead of using the master branch, if you want to be extra safe, like that: `git checkout go1.11.2`

4. You compile the actual Go that Raspberry Pi will use now:
    1. `cd src`
    2. `./make.bash`
    3. This will take some time, so be patient.

5. (Optional) Test your Go installation:
    1. `cd .. ; cd bin; nano hello.go`
    2. You paste in the following:
    
        ```go
        package main

        import "fmt"

        func main() {

                fmt.Printf("It woooooooooorks!\n")

        }
        ```

    3. Now do `./go run hello.go` and output should be `It woooooooooorks!`.


7. Set your environment ready to GO:
    1. `export PATH="$PATH:/home/pi/src/go/bin"`
    2. `export GOPATH=$HOME/go`
    
8. Check if PATH is set correctly: `go version`
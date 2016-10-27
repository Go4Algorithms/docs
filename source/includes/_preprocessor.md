## Go Complexity Graph Preprocessor:
Link to Gist: https://gist.github.com/jposton96a/3a5017ea5e63df397c2cece08f6f1d9e

### What is it?
The complexity preprocessor modifies the code submitted by the user so that the standard playground engine returns coordinate pairs mapping n-values to the time it takes the function to complete. This data will later be graphed using GoNum

The preprocessor reads code in through standard input and writes to standard output. The basic example provided uses the following steps to modify code:

1. Splits the code at each function declaration to obtain an array of functions
2. Parses each function to generate a list of function names
3. Selects the function to be tested by finding the first function name that starts with "Complexity"
4. If a main function exists in the code, renames the function to "main2"
5. Inserts new main function onto end of code

### Setup instructions:
In order to test this you will need a working Go playground docker setup.

```bash

git clone https://github.com/golang/playground.git`
cd playground
# You may need to modify sandbox/DockerFile by adding the following lines (uncommented)
# at line 45 before "# Add and compile tour packages"
# RUN apt-get update
# RUN apt-get install -y ca-certificates
docker build -t sandbox sandbox/
docker run -d -p 8080:8080 sandbox
cd sandbox
wget https://gist.githubusercontent.com/jposton96a/3a5017ea5e63df397c2cece08f6f1d9e/raw/8ca9e34070874cb0d935227fdd129ef56b3c8feb/processor.go

```

Now you should be able to test running and compiling code through the docker environment:

```bash

cat /path/to/code.go | go run ./sandbox/client.go | curl --data @- 172.17.0.1:8080/compile

```

Now, in order to use the preprocessor, simply run the code through processor.go before passing it to the playground client:

```bash

cat /path/to/code.go | go run ./sandbox/processor.go | go run ./sandbox/client.go | curl --data @- 172.17.0.1:8080/compile

```

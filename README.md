## module initialization and dependencies listing are already done in go.mod so directly manage dependencies
go mod tidy

## Normal build
go build -o s3copier copier.go

## Specific Build
GOOS=linux GOARCH=amd64 go build -o s3copier-linux copier.go

## Usage
export AWS_PROFILE=<profile> # set if you need to use a non-default profile.
export AWS_REGION=<region> 
./s3copier -bucket=<bucketname> -baseDir=<path> -concurrency=<number of concurrent connections to use> -queueSize=<number of keys to queue up to copy>

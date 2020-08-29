


## JDK runtime

*deploy to AWS jdk runtime*
```
sam package --template-file build/sam.jvm.yaml --output-template-file packaged.yaml --s3-bucket quarkus-brian
# then
sam deploy --template-file /Users/chylomicronman/git-repos/quarkus-lambda/packaged.yaml --capabilities CAPABILITY_IAM --stack-name quarkus-fruits-api
```

## Native binary custom runtime

*build native with docker*
```
./gradlew build -Dquarkus.package.type=native -Dquarkus.native.container-build=true
```

*start api NATIVE binary*
```
sam local start-api --template target/sam.native.yaml
```

*deploy to AWS native binary*
```
sam package --template-file build/sam.native.yaml --output-template-file packaged.yaml --s3-bucket quarkus-brian
# then
sam deploy --template-file /Users/chylomicronman/git-repos/quarkus-lambda/packaged.yaml --capabilities CAPABILITY_IAM --stack-name quarkus-native-fruits-api
```
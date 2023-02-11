1. aws iam create-role --role-name lambda-ex --assume-role-policy-document '{"Version:" "2012-10-17", "Statement": [{"Effect": "Allow", "Principal": {"Service": "lambda.amazonaws.com"}, "Action": "sts:AssumeRole"}]}'
2. GOOS=linux go build main.go
3. zip function.zip main
4. aws lambda create-function --function-name aws-lambda --zip-file fileb://function.zip --handler main --runtime go1.x --role arn:aws:iam::864311660456:role/lambda-ex
5. aws lambda invoke --function-name aws-lambda --cli-binary-format raw-in-base64-out --payload '{"What is your name?": "Jim", "How old are you?": 33}' output.txt
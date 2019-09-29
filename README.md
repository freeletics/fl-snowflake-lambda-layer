# FL-Snowflake-lambda-layer

In this Repo, we will install the common 3rd python libraries that will be shared between several lambda functions.

Here is the steps to package it:

python/lib/python3.7/site-packages

```shell script
mkdir -p lambda_layers/python/lib/python3.7/site-packages
virtualenv venv
python3 -m venv venv
source venv/bin/activate
# 1) install the dependencies in the desired folder
pip3 install  -r requirements.txt -t lambda_layers/python/lib/python3.7/site-packages/.
# 2) Zip the lambda_layers folder
cd lambda_layers
zip -r snowflake_lambda_layer.zip *
# 3) publish layer
aws lambda publish-layer-version \
    --layer-name fl-snowflake-lambda-layer \
    --compatible-runtimes python3.7 \
    --zip-file fileb://snowflake_lambda_layer.zip
```
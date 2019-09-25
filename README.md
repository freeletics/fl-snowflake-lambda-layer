# FL-Snowflake-lambda-layer

In this Repo, we will install the common 3rd python libraries that will be shared between several lambda functions.

Here is the steps to package it:

```shell script
virtualenv venv
python3 -m venv venv
source venv/bin/activate
pip3 install -r requirements.txt
deactivate
cd venv/lib/python3.7/site-packages
zip -r9 ${OLDPWD}/function.zip . -x \*.pyc ./python/pip\* ./python/setuptools\* ./python/wheel\* ./base_pkg\*;
cd $OLDPWD
aws lambda publish-layer-version --layer-name fl-snowflake-lambda-layer --zip-file fileb://function.zip
```
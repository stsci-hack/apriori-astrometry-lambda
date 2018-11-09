# apriori-astrometry-lambda
Lambda function for updating the a priori astrometry for HST images

Requirements:
AWS credentials
Docker
Code from https://github.com/spacetelescope/apriori-astrometry-lambda


Getting AWS credentials:
login to aws using aws-dsmo account and provided username (first time login will require a password change)
From top right menu find your account info and select "My Security Credentials" from drop-down menu
From left side menu select users (list of dsmo user accounts will appear)
Click on your username in this list (summary will appear)
Select "Security credentials" tab
You can ignore the existing Access key (auto created wih account but you don't have info needed to use it)
Click on "Create access key" and follow instructions to save/download keys.

Building Docker function:
>git clone https://github.com/spacetelescope/apriori-astrometry_lambda.git
>docker pull amazonlinux:2017.09
>docker run -v "$PWD":/outputs -it amazonlinux:2017.09 /bin/bash /outputs/build.sh	(on windows substitute $PWD with %cd%)

Testing locally:
create subdir /venv, copy venv.zip to it and unpack
cd into /venv

>docker run --rm -e AWS_ACCESS_KEY_ID='xxx' -e AWS_SECRET_ACCESS_KEY='xxx' -v "$PWD":/var/task lambci/lambda:python3.6 process.handler '{"s3_output_bucket": "dsmo-lambda-test-outputs", "fits_s3_key":"hst/public/icsc/icsca0voq/icsca0voq_drz.fits", "fits_s3_bucket":"stpubdata"}'

Installing on AWS:
??

Running on AWS:
??
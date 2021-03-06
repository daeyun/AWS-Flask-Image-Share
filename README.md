AWS-Flask-Image-Share
=====================

An image sharing app deployed on AWS Elastic Beanstalk

![Simple Image Sharer Screenshot](./docs/img/screenshot.png)

## Install AWS Elastic Beanstalk

####Linux

```
mkdir ~/aws-tools
cd ~/aws-tools
wget https://s3.amazonaws.com/elasticbeanstalk/cli/AWS-ElasticBeanstalk-CLI-2.6.0.zip
unzip AWS-ElasticBeanstalk-CLI-2.6.0.zip
rm AWS-ElasticBeanstalk-CLI-2.6.0.zip
export PATH=$PATH:~/aws-tools/AWS-ElasticBeanstalk-CLI-2.6.0/eb/linux/python2.7/
```

####Mac

```
mkdir ~/aws-tools
cd ~/aws-tools
wget https://s3.amazonaws.com/elasticbeanstalk/cli/AWS-ElasticBeanstalk-CLI-2.6.0.zip
unzip AWS-ElasticBeanstalk-CLI-2.6.0.zip
rm AWS-ElasticBeanstalk-CLI-2.6.0.zip
export PATH=$PATH:~/aws-tools/AWS-ElasticBeanstalk-CLI-2.6.0/eb/macosx/python2.7/
```

####Windows

See http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_Python_flask.html

Or use the web interface https://console.aws.amazon.com/elasticbeanstalk/home

## Clone this repository

Location doesn't matter. For example, `mkdir ~/flask_apps && cd ~flask_apps`

```
git clone https://github.com/daeyun/AWS-Flask-Image-Share.git
cd AWS-Flask-Image-Share
git add .
```

#### Making sure you don't accidentally commit config.py

```
git update-index --assume-unchanged config.py
```

## Configure the App

Create and enter your AWS security credentials in config.py. https://console.aws.amazon.com/iam/home?#security_credential
Change the following lines.

```
AWS_ACCESS_KEY_ID = 'your aws access key id'
AWS_SECRET_ACCESS_KEY = 'your aws secret access key'
```

## Configure AWS Elastic Beanstalk

```
eb init
```

Then enter your AWS Key ID and Access Key. Details here: http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_Python_flask.html

## Create Application

```
eb start
```

### View Application

```
eb status --verbose
```


## Update Application before Deploying into Production

In application.py, change the USE_S3 variable to True.
And remove the following line:

```
application.debug = True
```

Commit

```
git commit -am "Disable debugging and turn on S3"
```

### Deploy

```
git aws.push
```

You can also use https://console.aws.amazon.com/elasticbeanstalk

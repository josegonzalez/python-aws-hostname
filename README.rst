=============
aws-hostname
=============

Outputs a valid hostname for a given AWS instance

Installation
============

Using PIP via PyPI::

    pip install aws-hostname

Using PIP via Github::

    pip install git+git://github.com/josegonzalez/python-aws-hostname.git#egg=aws-hostname

Usage
=====

CLI Usage is as follows::

usage: aws-hostname [-h] [-i EC2_INSTANCE_ID] [-r EC2_REGION]
                    [-a AWS_ACCESS_KEY_ID] [-s AWS_SECRET_ACCESS_KEY]
                    [-t AWS_TAG] [-n] [-u] [-d]

You can also use the equivalent environment variables in place of command arguments.

This command will use the instance id and the tag ``aws:autoscaling:groupName`` to construct a valid hostname. It is useful for setting readable hostnames for autoscale groups like so::

    aws-hostname -r $REGION -a $ACCESS_ID -s $SECRET_KEY -i $INSTANCE_ID > /etc/hostname
    hostname -F /etc/hostname
    
You can also run it with the -u flag to connect using IAM profile instead of the access/secret key.

In cases where it is run against a non-autoscale group node, it will fallback to the ``Name`` attribute of the instance.

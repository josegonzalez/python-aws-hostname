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

    aws-hostname [-h] [-r EC2_REGION] [-s AWS_SECRET_ACCESS_KEY]
                     [-s AWS_SECRET_ACCESS_KEY] [-i EC2_INSTANCE_ID]

You can also use the equivalent environment variables in place of command arguments.

This command will use the instance id and the tag ``aws:autoscaling:groupName`` to construct a valid hostname. It is useful for setting readable hostnames for autoscale groups like so::

    aws-hostname -r $REGION -a $ACCESS_ID -s $SECRET_KEY -i $INSTANCE_ID > /etc/hostname
    hostname -F /etc/hostname

In cases where it is run against a non-autoscale group node, it will fallback to the ``Name`` attribute of the instance.

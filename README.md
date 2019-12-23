# Purpose

Demonstrate how to inject an AWS Elastic Beanstalk environment's EC2 hostname into a single container application. 

Note - I only tested this approach in a single-container Beanstalk environment. It's possible the file(s) and approach may need to be modified if you're using a multi-container environment.

## Background

This solution was based on the advice from: 
https://stackoverflow.com/questions/28698061/setting-docker-container-hostname-on-elastic-beanstalk

An alternative approach would be to invoke a shell script in your Dockerfile via `CMD` or `ENTRYPOINT`, and then have that shell script set and export an environment variable. An example of this approach is available at: 
https://github.com/matwerber1/aws-ec2-host-to-beanstalk-docker-container-env-var

## Notes

If your Dockerfile declares an env var using the `ENV` command and you use the `--env` flag to declare a variable of the same name in your `docker run` command, `docker run --env` will override `ENV`.

# Using Amazon Web Services (AWS)

## tl;dr

- Our sign-in URL: `https://savaslabs.signin.aws.amazon.com/console`
- Root user email/pass are in 1Password under `AWS root user`
- Individuals (staff & contractors) are issued AWS Access Key IDs and Secret Access Keys via [IAM](https://console.aws.amazon.com/iam/home#/home)
  - Ask internally if you need help creating a user/group/policy

## Services we use

- [IAM](https://console.aws.amazon.com/iam/home#/home), for managing users, groups, and permissions
- [S3](https://console.aws.amazon.com/s3/home), for sharing files

## Managing users

Those with relevant permissions may visit [IAM](https://console.aws.amazon.com/iam/home?region=us-east-1) and create/modify users, groups and policies. It's a good idea to copy existing policies and add to existing groups if possible.

### Policies

Generally speaking, try to assign policies that give the minimum set of permissions needed to perform a task. For example if a user (machine or human) needs access to download the seed database from a directory in a bucket, this will suffice:

``` json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::{bucket-name}/seed-database/*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::{bucket-name}/seed-database/*"
            ]
        }
    ]
}
```

n.b. the above will _not_ allow the user to do `aws s3 ls` on that directory, but `aws s3 cp` will work.

## Testing locally

If you add a new user, you'll get an Access Key ID and a Secret Access Key. You may simulate their access by running this in your terminal:

```
export AWS_ACCESS_KEY_ID={id}
export AWS_SECRET_ACCESS_KEY={secret}
```

Then run whatever commands you need (e.g. `make install`). After you've confirmed that the user permissions work for your needs, you can store them or transmit them securely to whoever needs to use them.

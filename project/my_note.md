[cloudshell-user@ip-10-4-179-32 ~]$ aws ec2 create-restore-image-task --object-key ami-0ec6fdfb365e5fc00.bin --bucket udacity-srend --name "udacity-sonnh65"
{
    "ImageId": "ami-0830f9688302023ba"
}

[cloudshell-user@ip-10-4-179-32 ~]$ aws ec2 copy-image --source-image-id "ami-0830f9688302023ba" --source-region us-east-1 --region us-east-2 --name "udacity-sonnh65"
{
    "ImageId": "ami-0e2c18249185ce087"
}

[cloudshell-user@ip-10-4-179-32 ~]$ aws ec2 copy-image --source-image-id "ami-0830f9688302023ba" --source-region us-east-1 --region us-west-1 --name "udacity-sonnh65"
{
    "ImageId": "ami-01a3d148c8ae2c996"
}

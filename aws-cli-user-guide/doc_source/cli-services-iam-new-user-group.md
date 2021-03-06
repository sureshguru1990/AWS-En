Creating IAM Users and Groups
This topic describes how to use AWS Command Line Interface (AWS CLI) commands to create an IAM group and a new IAM user, and then add the user to the group.

Before you run any commands, set your default credentials. For more information, see Configuring the AWS CLI.

To create an IAM group and add a new IAM user to it

Use the https://docs.aws.amazon.com/cli/latest/reference/iam/create-group.html command to create the group.

$ aws iam create-group --group-name MyIamGroup
{
    "Group": {
        "GroupName": "MyIamGroup",
        "CreateDate": "2018-12-14T03:03:52.834Z",
        "GroupId": "AGPAJNUJ2W4IJVEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:group/MyIamGroup",
        "Path": "/"
    }
}
Use the https://docs.aws.amazon.com/cli/latest/reference/iam/create-user.html command to create the user.

$ aws iam create-user --user-name MyUser
{
    "User": {
        "UserName": "MyUser",
        "Path": "/",
        "CreateDate": "2018-12-14T03:13:02.581Z",
        "UserId": "AIDAJY2PE5XUZ4EXAMPLE",
        "Arn": "arn:aws:iam::123456789012:user/MyUser"
    }
}
Use the https://docs.aws.amazon.com/cli/latest/reference/iam/add-user-to-group.html command to add the user to the group.

$ aws iam add-user-to-group --user-name MyUser --group-name MyIamGroup
To verify that the MyIamGroup group contains the MyUser, use the https://docs.aws.amazon.com/cli/latest/reference/iam/get-group.html command.

$ aws iam get-group --group-name MyIamGroup
{
    "Group": {
        "GroupName": "MyIamGroup",
        "CreateDate": "2018-12-14T03:03:52Z",
        "GroupId": "AGPAJNUJ2W4IJVEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:group/MyIamGroup",
        "Path": "/"
    },
    "Users": [
        {
            "UserName": "MyUser",
            "Path": "/",
            "CreateDate": "2018-12-14T03:13:02Z",
            "UserId": "AIDAJY2PE5XUZ4EXAMPLE",
            "Arn": "arn:aws:iam::123456789012:user/MyUser"
        }
    ],
    "IsTruncated": "false"
}

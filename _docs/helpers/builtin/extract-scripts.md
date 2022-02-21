---
title: Extract Scripts
nav_text: Extract Scripts
categories: builtin-helpers
---

Often it is useful to be able to upload custom scripts to the server and run them. One way to do this is first to upload the scripts to s3 and then download them down to the server as part of the user-data script.  Lono supports this deployment flow with the `scripts` folder.  Files added to the `scripts` folder get tarballed up and uploaded to the lono s3 bucket.

## extract_scripts helper

Lono provides a `extract_scripts` helper that you can include your `user_data` scripts to extract the `scripts` files in your lono blueprint to `/opt/scripts` on the server.  Here's an example:

app/blueprints/demo/user_data/bootstrap.sh

    #!/bin/bash -exu

    <%= extract_scripts(to: "/opt") %>

    SCRIPTS=/opt/scripts
    $SCRIPTS/install_stuff.sh

In order to use extract_scripts, you'll need scripts in the `scripts` folder. We'll add a test script:

app/blueprints/demo/scripts/install_stuff.sh

    yum install -y jq

## lono user_data command

Typically, the `user_data` scripts are embedded in your CloudFormation templates with the `user_data` helper method.  You can see the generated script with [lono build](/reference/lono-build/) and looking at the template in the `output` folder.

The `lono user_data` command is also provided so you can see the code that `extract_script` helper produces.

Here's an example:

    $ lono user_data bootstrap
    Detected scripts
    Tarballing scripts folder to scripts.tgz
    => cd app/blueprints/demo && dot_clean .
    => cd app/blueprints/demo && tar -c scripts | gzip -n > scripts.tgz
    Tarball created at output/scripts/scripts-93b8b29b.tgz
    Building user_data for 'bootstrap' at ./user_data/bootstrap.sh
    #!/bin/bash -exu

    # Generated from the lono extract_scripts helper.
    # Downloads scripts from s3, extract them, and setup.
    mkdir -p /opt
    aws s3 cp s3://mybucket/path/to/folder/dev/scripts/scripts-93b8b29b.tgz /opt/
    cd /opt
    tar zxf /opt/scripts-93b8b29b.tgz
    chown -R ec2-user:ec2-user /opt/scripts

    SCRIPTS=/opt/scripts
    $SCRIPTS/install_stuff.sh
    $

## MD5 Checksum

Notice, that the name of the scripts tarball includes an md5 checksum.  Lono first generates a `scripts.tgz`, computes the file's md5sum and then renames it to include the md5sum.  There's a very good reason for this.

Whenever you make changes in your `scripts` folder and update your CloudFormation templates, CloudFormation does not see the changes.  If the same `scripts.tgz` s3 url were used then CloudFormation would not know that it needed to update the EC2 instance that uses the user-data script.  By including the md5 checksum in the file name, this changes the user-data script, and  this lets CloudFormation know that the scripts have changed.

r-n-w.github.io

This is my personal website showcasing some of my work and qualifications. This is the fastest way to get a sense of where my skills are at. If you like what you see don't hesitate to reach out about work opportunities.


#!/bin/bash
TARGET="/home4/ryannath/public_html/site"
GIT_DIR="/home4/ryannath/website.git"
BRANCH="master"
echo 'this script ran'
while read oldrev newrev ref
do
  	# only checking out the master (or whatever branch you would like to deploy)
        if [ "$ref" = "refs/heads/$BRANCH" ];
        then
            	echo "Ref $ref received. Deploying ${BRANCH} branch to production..."
                git --work-tree=$TARGET --git-dir=$GIT_DIR checkout -f $BRANCH
        else
            	echo "Ref $ref received. Doing nothing: only the ${BRANCH} branch may be deployed on this server."
        fi
done


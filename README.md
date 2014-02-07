openshift-mongo-flask-example
=============================

NOTE this will not work in the recent versions of OpenShift Online because the environment variables are not correct in myflaskapp.py. If you want to fix them and give me a pull request it would be much appreciated. K THX BYE
===============

This is the code to go along with the [OpenShift blog piece](https://openshift.redhat.com/community/blogs/rest-web-services-with-python-mongodb-and-spatial-data-in-the-cloud) on how to use Flask (python) with MongoDB to create a REST like web service with spatial data

Running on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/

Create a python-2.6 application and add a MongoDB cartridge to the app

    rhc app create -a pythonws -t python-2.6
    rhc app cartridge add -a pythonws -c mongodb-2.0

Add this upstream flask repo


    cd pythonws
    git remote add upstream -m master git://github.com/openshift/openshift-mongo-flask-example.git
    git pull -s recursive -X theirs upstream master
    
Then push the repo upstream

    git push
    
To add the data to the MongoDB instance please follow the instructions on this blog:
[Mongo Spatial on OpenShift](https://openshift.redhat.com/community/blogs/spatial-mongodb-in-openshift-be-the-next-foursquare-part-1)

Be sure to:

- add the data to a collection called parkpoints
- create the spatial index on the documents

Once the data is imported you can now checkout your application at:

    http://pythonws-$yournamespace.rhcloud.com
    
    


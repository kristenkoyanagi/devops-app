# WCF DevOps Homework

## Overview
Your mission, should you choose to accept it, is deploy and scale two applications (Web API and Data API) to incoming requests.

## Tasks

- Deploy the sample python applications to a cluster of nodes using a container orchestration framework
- Web API should be publicly accessible over HTTPS
- Auth API should NOT be accessible via the public internet
- Please show how you would auto-scale the number of nodes and containers as the number of requests increases

## Deliverables

Have the following ready to share with folks:

- A Dockerfile for each application
- Framework for deploying containers to a group of nodes
- Documentation on continuous delivery process to ship to a production environment
- Scripts and/or docs involved with automatically scaling the application and nodes horizontally based on requests

For your work, DO NOT fork this repo!  Create a new repo using public Github or Gitlab account, use a unique name and send us the final product!


## Notes

- Again, please do NOT fork or submit a PR to this repo!
- It's perfectly fine to show your work through git commits (using well written commit messages)
- You are welcome to change the python applications and their requirements in any way you see fit
- We are purposefully NOT being overly prescriptive in this assignment
- Thinking creatively about the solution is encouraged
- This assignment should take less than 3 hours to complete
- If you get stuck or need more information, please reach out for clarity
- We will review your submission and be in touch with next steps.
- Have fun!

## Getting Started in Local Development

This assumes you have `ab`, `sqlite3`, `python`, `pip`, `virtualenv` already installed.  If not (and running Ubuntu) you can use:
```
sudo apt-get install apache2-utils sqlite3 python3-pip
pip3 install virtualenv 
```

Please create and source your virtualenv before beginning; something like:
```
virtualenv -p python3 homework
source homework/bin/activate    # or python3 -m venv myenv
```

Initialize the database (only needs to be done once):
```
sqlite3 database.db < schema.sql
```

Running the apps locally:
```
pip install -r requirements.txt
python web_api.py
python auth_api.py
```

Making a request
```
curl -X POST -H 'Authorization: wcftoken' http://127.0.0.1:5000/check
```

Simulating a lot of requests
```
ab -m POST -H "Authorization: wcftoken" -n 500 -c 4 http://127.0.0.1:5000/check
```
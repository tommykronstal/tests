# Course managements tests in automated pipeline

In addition to tests in the students repo, the course management can add extra tests in a repo like this that will further test the students implementation.  

The test file(s) are placed in the root of the tests repo and should be named [testname].test.js where testname can be anything other than the same name as the test files in the students repo. These files will all be placed in the same folder when the pipeline runs.  

This repo must also contain a Dockerfile-override, this is the file that will be used in the pipeline to perform the tests. The reason behind the naming is that if there already is a Dockerfile in the repo it will be ignored. The Dockerfile-override can have the exact same content as the original Dockerfile and the most simple example of it is just using a slightly modified example from Node.js guide [Dockerizing a Node.js web app](https://nodejs.org/en/docs/guides/nodejs-docker-webapp/)

~~~
FROM node:carbon

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./

RUN npm install
# If you are building your code for production
# RUN npm install

# Bundle app source
COPY . .

CMD [ "npm", "test" ]
~~~

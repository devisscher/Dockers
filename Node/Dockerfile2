# This docker file is for a node app which needs to run webpack.

FROM node:8
# Create app directory

# Instal global deps
RUN npm install webpack -g
RUN npm install pm2 -g


WORKDIR /tmp
COPY package.json /tmp/
RUN npm config set registry http://registry.npmjs.org/ && npm install

WORKDIR /usr/src/app
COPY . /usr/src/app/
RUN cp -a /tmp/node_modules /usr/src/app/
RUN webpack

ENV NODE_ENV=production

EXPOSE 3000
CMD ["pm2-docker", "process.yml"]
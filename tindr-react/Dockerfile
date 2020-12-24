FROM node:lts-alpine3.12
# set working directory
WORKDIR /app

# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH

# install app dependencies
COPY package.json ./
COPY yarn.lock ./
RUN yarn add react-scripts
RUN yarn install --silent

# add app
COPY . ./

# start app
CMD ["yarn", "start"]

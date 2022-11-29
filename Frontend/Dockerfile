FROM node:14.18.1-alpine

# install simple http server for serving static content
RUN npm install -g http-server

# make the 'app' folder the current working directory
WORKDIR /app

# copy both 'package.json' and 'package-lock.json' (if available)
COPY package*.json ./

RUN npm install npm@latest -g

# install project dependencies

RUN npm install

# copy project files and folders to the current working directory (i.e. 'app' folder)
COPY . .

RUN npm install -D webpack-cli -y

# build app for production with minification
RUN npm run build

RUN npm install webpack@5.75.0 --force

EXPOSE 8080
CMD [ "http-server", "dist" ]



# cmt
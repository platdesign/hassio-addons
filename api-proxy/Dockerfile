FROM mhart/alpine-node

# Create app directory
WORKDIR /usr/src

RUN apk add --no-cache git

RUN git clone https://github.com/platdesign/hassio-addon-api_proxy.git .

WORKDIR /usr/src/app

RUN npm install --production

ENV NODE_ENV=production

EXPOSE 8080
CMD [ "npm", "start" ]

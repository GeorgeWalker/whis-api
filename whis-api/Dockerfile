FROM node:14.16.0

WORKDIR /app

# make sure the linux ocp command line tools executable exists first
# copy necessary files to image
COPY oc /app
COPY package*.json /app
COPY tsconfig.json /app
COPY src/ /app/src
COPY nodemon.json /app

# setup envirnment variables
RUN touch /app/.env
RUN echo "POSTGRES_SERVER_PORT=5432\nPOSTGRES_SERVER_HOST=localhost\nPOSTGRES_USER=whis\nPOSTGRES_DB=whis\nTESTING_USERS=true\nNODE_ENV=test\nROLLBACK=true" > /app/.env

# install depedencies
RUN npm install

RUN npm run build
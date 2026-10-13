# FROM node:20
# WORKDIR /opt/server/
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue" 
# CMD ["node", "server.js"]

FROM node:20.19.5-alpine3.22 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

# docker best practices as we are using two images it reducess the and optimize the images this on
# called as mulitsatage build as one images for build another images as final image.
FROM node:20.19.5-alpine3.22
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue" 
CMD ["server.js"]
ENTRYPOINT ["node"]





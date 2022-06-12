# Using Multi-Stage Docker
# # Stage 1 # #

# lets pull the node base image / node ver.16 for some reason seems to be stable for this code
FROM node:16 AS stage1

# set the working directory
WORKDIR /app

# adding node module path
ENV PATH /app/node_modules/.bin:$PATH

# copy over the package.json inside the docker env
COPY package.json .

# install node packages inside the docker env 
RUN npm install

# copy over the files inside the docker env
COPY . .

# optimize packages
RUN npm run build

# # Stage 2 # #

# lets pull the nginx base image
FROM nginx:stable


# set the working directory
WORKDIR /usr/share/nginx/html

# Remove default nginx static resources
RUN rm -rf ./*

# Copies static resources from builder stage
COPY --from=stage1 /app/build .


# define entry
#ENTRYPOINT [ "nginx","-g","daemon off;" ]


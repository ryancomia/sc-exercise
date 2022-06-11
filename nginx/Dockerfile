# pull the official nginx stable
FROM nginx:stable-alpine


# Set working directory to nginx resources directory
WORKDIR /usr/share/nginx/html

# Remove default nginx static resources
RUN rm /etc/nginx/conf.d/default.conf

# Copies static resources from build stage
COPY nginx.conf /etc/nginx/conf.d/

EXPOSE 80

# nginx with global directives and daemon off
ENTRYPOINT ["nginx", "-g", "daemon off;"]
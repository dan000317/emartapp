FROM node:14 AS web-build
WORKDIR /usr/src/app
COPY ./ ./client
# DAN: check with the developer or in the internet how to build the application artifact
RUN cd client && npm install && npm run build --prod

# Use official nginx image as the base image
FROM nginx:latest

# DAN: check with the developer or in the internet where the application artifact is stored
# DAN: check the documentation of nginx where to store the html file  
# Copy the build output to replace the default nginx contents.
COPY --from=web-build /usr/src/app/client/dist/client/ /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 4200
EXPOSE 4200

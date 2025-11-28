################################
# Stage 1 - Build Angular app
################################
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .

# Adjust if your build command is different
RUN npm run build --prod

################################
# Stage 2 - Serve with Nginx
################################
FROM nginx:alpine

# Remove default Nginx static content
RUN rm -rf /usr/share/nginx/html/*

# Copy built Angular files
# For Angular 13+ default output path is "dist/<project-name>"
# Replace <project-name> with actual folder under dist
COPY --from=build /usr/src/app/dist/angular-15-crud /usr/share/nginx/html

# Expose port 80 (Nginx)
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

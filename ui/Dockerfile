FROM node:10-alpine as build
WORKDIR /build
COPY . .
RUN NG_CLI_ANALYTICS=ci npm install -g @angular/cli
RUN NG_CLI_ANALYTICS=ci npm install
RUN ng --version
RUN ng build
RUN ls -al dist

FROM nginx:alpine
WORKDIR /app
COPY --from=build /build/dist/TeamAPoolProjectUI .
COPY nginx.conf /etc/nginx/nginx.conf

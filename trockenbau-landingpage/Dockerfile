FROM hugomods/hugo:base-0.159.1 AS build

WORKDIR /src
COPY trockenbau-landingpage/ .
COPY themes/ /themes/
RUN hugo --minify --cleanDestinationDir

FROM nginx:1.27-alpine

COPY trockenbau-landingpage/nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /src/public /usr/share/nginx/html

EXPOSE 80

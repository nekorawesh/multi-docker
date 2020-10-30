FROM node:alpine as builder

WORKDIR /usr/app

COPY ./package.json ./

RUN npm run install

COPY ./ ./

CMD [ "npm", "run", "build" ]

FROM nginx

EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=0 /usr/app/build /usr/share/nginx/html
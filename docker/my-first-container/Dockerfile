FROM node:20
WORKDIR /usr/app
COPY . .
RUN npm install
EXPOSE 3000
USER node
CMD ["npm", "start"]

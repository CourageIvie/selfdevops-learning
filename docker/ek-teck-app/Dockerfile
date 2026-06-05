FROM node:18-slim
RUN apt-get update -y && \
    apt-get install -y wget unzip && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
WORKDIR /usr/app
RUN wget https://group5-braincells.s3.amazonaws.com/node-ex-website.zip && \
    unzip node-ex-website.zip && \
    cp -r node-ex-website/* . && \
    rm -rf node-ex-website.zip node-ex-website && \
    npm install
EXPOSE 3000
VOLUME ["/usr/app/data"]
USER node
CMD ["npm", "start"]

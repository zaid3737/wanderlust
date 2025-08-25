#stage 1
FROM Node:21 as backend-builder

#setting up work directory
WORKDIR /app

# copying the code
COPY . .

# packages installer
RUN npm i

# tests
RUN npm run test

#stage 2
FROM Node:21-slim

# working directory
WORKDIR /app

# copy the above stage as compressed.
COPY --from=backend-builder /app .

COPY .env.docker .env

#port 
EXPOSE 5000

# App
CMD ['npm', 'start']


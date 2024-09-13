# # docker build -t ronaldojssilva/simulador-do-caos:v1 -f src/Dockerfile src/
# # docker tag ronaldojssilva/simulador-do-caos:v1 ronaldojssilva/simulador-do-caos:latest

# # docker container un -d -p 8080:3000 --restart=on-failure ronaldojssilva/simulador-do-caos:v1

# # docker build -t ronaldojssilva/simulador-do-caos:v2 -f src/Dockerfile src/

FROM node:20.9.0
WORKDIR /app
COPY package*.json ./
RUN npm install
RUN apt update && apt install stress --yes
COPY . .
RUN npm run compile
HEALTHCHECK --interval=5s --timeout=3s --start-period=5s --retries=1 CMD [ "curl", "-f", "http://localhost:3000/health" ]
EXPOSE 3000
CMD ["npm", "start"]

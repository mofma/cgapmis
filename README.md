Frontend
----------------
Getting Started
Prerequisites
  Node.js (v16 or higher)
  npm (Node Package Manager)
Set environment variables
  cp example.env .env
  set your variables
Installation & Running
  Install dependencies:
     npm install
  Run the development server:
     npm run dev

BTC backend
Additional programs
Taskfile (Optional)
docker-compose or podman-compose
Postman
How to run
Run go mod download command to download dependencies

go mod download
Copy the .env.example file to .env and change variables to what you need

cp .env.example .env && nano .env
Start the postgres database

ⓘ NOTE: If you're starting the program by running the taskfile command, you can skip this step because DB will start up automatically, and it does not need additional configuration.

export POSTGRES_PORT=5432 POSTGRES_USER=postgres POSTGRES_PASSWORD=postgres POSTGRES_DB=btc
cd containers && docker-compose -f database.yml up -d && cd ..
Or use next taskfile command:

task db
Start the keycloak

export KEYCLOAK_PORT=1141 KEYCLOAK_ADMIN=user KEYCLOAK_ADMIN_PASSWORD=bitnami
cd containers && docker-compose -f keycloak.yaml up -d && cd ..
Or use next taskfile command:

task kc
Configure keycloak and paste KEYCLOAK_CLIENT_ID and KEYCLOAK_CLIENT_CREDENTIALS variables to .env file

Run the following command to start server:

go run main.go
Or you can run Run configuration if you are using Goland

Or you can run the following taskfile command:

task run
Import BTC collection and BTC-Local environment into Postman program

Send request throw Postman

     

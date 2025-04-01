# RemitlyInternshipTask
# SWIFT Codes API

## Project Description
This project is a REST API for storing and sharing SWIFT data from a file. The application uses **TypeScript**, **Node.js**, **Express**, **Prisma** and **PostgreSQL**. **Prisma** was chosen for its strong type safety and developer-friendly API, which makes working with databases in TypeScript and JavaScript projects more efficient and error-free. Its powerful features like automatic migrations, performance optimization, and flexibility in supporting multiple databases make it an ideal choice for modern applications. The whole thing is not containerized using **Docker**, I couldn't get this step right.

1. **Download the file from the Releases**
- Download the **SwiftCodes.zip** file, then unzip it.
- Open the command line and navigate to the project folder named SwiftCodes by:
```cmd
cd "PATH"
```
- You can minimize the command line for now

2. **Prerequisites**
Before starting the project, make sure you have installed:
- [Node.js](https://nodejs.org/en)

Then create an account on the website:
- [Prisma](https://www.prisma.io/)
Then follow the instructions on the website:
- click **New project**
- Set **Name**
- click **Choose your starting product**>>**Prisma Postgres**>>**Get started**
- select the **EUROPE** region
- after a while the database status should change from **PROBISIONING** to **CONNECTED** (Try refreshing the page)
- then go to the **Setup** tab and in the **Configure your database access** click **Generate database credentials**
- copy the generated .env file content and replace existing line in your **.env** file located in the folder **SwiftCodes** to copied/generated line.

3. **Using API Endpoints**
- While in the SwiftCodes folder, type and run:
```cmd
npx ts-node src/index.ts
```
- You will probably be asked to download additional packages, type y (to agree), then type and run the command again.
- Now you can open another command line (leave the previous one open with the server running), go back to the SwiftCodes project folder using the **cd** command. This is where you will be able to test Endpoints and the RESTAPI GET, POST and DELETE methods.

**Method List**
| Method | Endpoint | Description |
|---------|---------------------------------------|-------------------------------------------|
| `GET` | `/v1/swift-codes/:swiftCode` | Gets bank or branch details |
| `GET` | `/v1/swift-codes/country/:countryISO2Code` | Gets all banks in a given country |
| `POST` | `/v1/swift-codes` | Adds a new bank or branch |
| `DELETE`| `/v1/swift-codes/:swiftCode` | Deletes a bank or branch |

Example **GET** query:
```cmd
curl -X GET http://localhost:8080/v1/swift-code/country/PL
```

Example **POST** query:
```cmd
curl -X POST http://localhost:8080/v1/swift-codes -H "Content-Type: application/json" -d '{"swiftCode": "TESTTESTXXX", "bankName": "TEST Name", "address": "TEST Address", "countryISO2": "PL", "countryName": "Poland", "isHeadquarter": true}'
```

Example **DELETE** query:
```cmd
curl -X DELETE http://localhost:8080/v1/swift-codes/TESTTESTXXX
```

If you want to terminate the script index.ts or any other .ts script, click **CTRL+C** while in the command line.

4. **Testing the Application**
To run integration tests, type and run the following command from the command line:
```cmd
npm test -- index.test.ts
```

To run unit tests, type and run the following command from the command line:
```cmd
npm test -- storeData.test.ts
```

If you want to terminate the index.ts script or any other .ts script, click **CTRL+C** while in the command line.

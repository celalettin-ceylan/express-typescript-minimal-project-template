# express + typescript minimal template project

1. Create app folder and npm init:
`mkdir node-express-typescript`
`cd node-express-typescript`
`npm init -y`

2. Install express, dotenv and create .env file at root directory:
`npm install express dotenv`

3. Write port number into .env file:
`PORT=8000`

4. Install ts and other other ts packages:
`npm i -D typescript @types/express @types/node`

5. Generating tsconfig.json
`npx tsc --init`

6. Edit output directory option line in tsconfig.json
```json 
{
  "compilerOptions": {
    "outDir": "/dist"
    // rest options remain same
  }
}
```

7. Create index.ts file in root directory and coppy/paste below code blocks
```javascript
import express, { Express, Request, Response } from 'express';
import dotenv from 'dotenv';

dotenv.config();

const app: Express = express();
const port = process.env.PORT;

app.get('/', (req: Request, res: Response) => {
  res.send('Express + TypeScript Server');
});

app.listen(port, () => {
  console.log(`⚡️[server]: Server is running at https://localhost:${port}`);
});
```
8. Install nodemon
`npm install -D concurrently nodemon`

9. Update the scripts in the package.json file:
```json
{
  "scripts": {
    "build": "npx tsc",
    "start": "node dist/index.js",
    "dev": "concurrently \"npx tsc --watch\" \"nodemon -q dist/index.js\""
  }
}
```


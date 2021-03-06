# NodePop Avanzado

[Demo](/anuncios) of the methods (this link works only if you run the project)

Api for the iOS/Android apps.

## Deploy

## AWS URL: 
 (I've used this backend instead of mine because is the one I used for the advanced react project, and some api urls are different)
 - Nodepop Back: http://ec2-18-224-212-77.us-east-2.compute.amazonaws.com/
 - Nodepop Front: http://18.224.212.77/

 To check the 'X-Owner' http header, check the 'style.css' file.

### Install dependencies  
    
    npm install

### Configure  

Review lib/connectMongoose.js to set database configuration

### Init database

    npm run installDB

## Start

To start a single instance:
    
    npm start

To start in development mode:

    npm run dev (including nodemon & debug log)

## Test

    npm test (pending to create, the client specified not to do now)

## ESLint

    npm run hints

## API v1 info


### Base Path

The API can be used with the path: 
[API V1](/apiv1/anuncios)

### Language

All requests that return error messages are localized to english, if you want to 
change language make the request with the header accept-language set to other language, 
i.e. Accept-Language: es 

### Error example

    {
      "ok": false,
      "error": {
        "code": 401,
        "message": "Authentication failed. Wrong password."
      }
    }

### GET /anuncios

**Input Query**: 

start: {int} skip records  
limit: {int} limit to records  
sort: {string} field name to sort by  
includeTotal: {bool} whether to include the count of total records without filters  
tag: {string} tag name to filter  
venta: {bool} filter by venta or not  
precio: {range} filter by price range, examples 10-90, -90, 10-   
nombre: {string} filter names beginning with the string  

Input query example: ?start=0&limit=2&sort=precio&includeTotal=true&tag=mobile&venta=true&precio=-90&nombre=bi

**Result:** 

    {
      "ok": true,
      "result": {
        "rows": [
          {
            "_id": "55fd9abda8cd1d9a240c8230",
            "nombre": "iPhone 3GS",
            "venta": false,
            "precio": 50,
            "foto": "/images/anuncios/iphone.png",
            "__v": 0,
            "tags": [
              "lifestyle",
              "mobile"
            ]
          }
        ],
        "total": 1
      }
    }


### GET /anuncios/tags

Return the list of available tags for the resource anuncios.

**Result:** 

    {
      "ok": true,
      "allowed_tags": [
        "work",
        "lifestyle",
        "motor",
        "mobile"
      ]
    }

👤 **Kiara Mendoza**

* Website: https://kiara-portfolio.netlify.app/
* Github: [@KiaraMendoza](https://github.com/KiaraMendoza)

## Show your support

Give a ⭐️ if this project helped you!

***
_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
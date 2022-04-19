# SINUS Webshop

## FIGMA DESIGN
[Webshop skiss](https://www.figma.com/proto/3UJwVLlNILObpHDRHbZrND/Sinus-webshop?node-id=21%3A2&scaling=min-zoom)

# SINUS Webshop - REST API

## Getting Started

1. `cd backend`
2. Install dependencies `npm install`
3. Start the server `npm run start`

## EndPoint Specifikation

| Resurs | Metod | Detaljer | Request Body |
| ------ | ------ | ------ | ------ |
| /api/auth/ | POST | Authentiserar user med email & password. Returnerar en JWT-token som används vid varje anrop API:et i en Authorization-header. | {"email": "...", "password" : "..."} |
| /api/register/ | POST | Registrerar en användare. | Se User-modellen |
| /api/products/ | GET | Returnerar en lista på samtliga produkter. | ❌ | 
| /api/products/:id | GET | Returnerar en enstaka produkt. | ❌ |
| /api/products/ | POST | Skapar en ny produkt. Enbart tillgänglig för admins | Se Product-modellen |
| /api/products/:id | PATCH | Uppdaterar produkt. Enbart tillgänglig för admins | Se Product-modellen |
| /api/products/:id | DELETE | Tar bort en produkt med :id. Enbart tillgänglig för admins | ❌ |
| /api/orders | GET | Returnerar en lista på den användarens ordrar eller samtliga ordrar för admins. | ❌ |
| /api/orders | POST | Skapar en ny order | Se Order-modellen |
| /api/me | GET | Hämtar den inloggade användren | ❌ |
| /api/me | PATCH | Uppdaterar profilen för den inloggade användren | Se User-modellen |

### Datamodeller

#### Product

##### Request Body
```javascript
 {
  "title": 'Gretas Fury',
  "price": 999,
  "shortDesc": 'Unisex',
  "longDesc": 'Skate ipsum dolor sit amet...',
  "imgFile": 'skateboard-greta.png'
} 
```

##### Document Model
```javascript
 {
  _id: '39y7gbbZk1u4ABnv', // generated serverside
  title: 'Gretas Fury',
  price: 999,
  shortDesc: 'Unisex',
  longDesc: 'Skate ipsum dolor sit amet...',
  imgFile: 'skateboard-greta.png' // Asset logic on clientside
} 
```

#### Order
##### Request Body
```js
{
  "items": ["productId1", "productId1", "productId2"]
}
```

##### Document Model
```javascript
 {
  _id: 123,
  timeStamp: Date.now(), 
  status: 'inProcess',
  items: [ 
    {
      title: "Tricky",
      price: 799,
      imgFile: "skateboard-generic.png",
      _id: "9E6KXMIdRglW0wbL",
      amount: 2
    }, 
    {
      <etc>
    }, 
    ... 
  ],
  orderValue: 999
} 
```

#### User

##### Request Body
```js
{
  "email": 'greta.thunberg@example.se',
  "password": 'grillkorv123',
  "name": 'Johan Kivi',

  "address": {
    "street": 'Tokitokvägen 3',
    "zip": '123 45',
    "city": 'Tokberga'
  }
} 
```

##### Document Model

```javascript
{
  _id: '6b521d3f-3d15...' // generated server side
  email: 'johan.kivi@zocom.se',
  password: '$$$hashed password$$$', // hashed serverside
  name: 'Johan Kivi',
  role: 'admin', // or customer
  address: {
    street: 'Tokitokvägen 3',
      zip: '123 45',
      city: 'Tokberga'
  },
  orderHistory: [ <orderId1>, <orderId2>, ... ]
} 
```


# MongoBD

Crear base de datos
•	Para crear la base de datos
use basededatos;
•	Para crear las colecciones
db.createCollection('productos');
db.createCollection('chat');

•	Para insertar las rows a productos
db.productos.insertMany([
    {
        "timestamp": ISODate(),
        "title": "Product 1",
        "price": 100,
        "description":"Some description for product 1",
        "code": "P1",
        "image": "Product1.com",
        "stock": 100
    },
    {
        "timestamp": ISODate(),
        "title": "Product 2",
        "price": 320,
        "description":"Some description for product 2",
        "code": "P2",
        "image": "Product2.com",
        "stock": 200
    },
    {
        "timestamp": ISODate(),
        "title": "Product 3",
        "price": 930,
        "description":"Some description for product 3",
        "code": "P3",
        "image": "Product3.com",
        "stock": 300
    },
    {
        "timestamp": ISODate(),
        "title": "Product 4",
        "price": 1140,
        "description":"Some description for product 4",
        "code": "P4",
        "image": "Product4.com",
        "stock": 400
    },
        {
        "timestamp": ISODate(),
        "title": "Product 5",
        "price": 1140,
        "description":"Some description for product 5",
        "code": "P5",
        "image": "Product5.com",
        "stock": 400
    },

	{
        "timestamp": ISODate(),
        "title": "Product 6",
        "price": 1140,
        "description":"Some description for product 6",
        "code": "P6",
        "image": "Product6.com",
        "stock": 400
    },
	{
        "timestamp": ISODate(),
        "title": "Product 7",
        "price": 1150,
        "description":"Some description for product 7",
        "code": "P7",
        "image": "Product7.com",
        "stock": 409
    },

	{
        "timestamp": ISODate(),
        "title": "Product 8",
        "price": 2390,
        "description":"Some description for product 8",
        "code": "P8",
        "image": "Product8.com",
        "stock": 409
    },

	{
        "timestamp": ISODate(),
        "title": "Product 9",
        "price": 390,
        "description":"Some description for product 9",
        "code": "P9",
        "image": "Product9.com",
        "stock": 489
    },

	{
        "timestamp": ISODate(),
        "title": "Product 10",
        "price": 3900,
        "description":"Some description for product 10",
        "code": "P10",
        "image": "Product10.com",
        "stock": 560
    }]);

•	Para insertar algunos carritos
db.chat.insertMany([{timestamp: ISODate()}, {timestamp: ISODate()}])
•	Para listar todos los productos
db.productos.find();
•	Para contar la cantidad de documentos en productos
db.productos.countDocuments();
•	Agregar otro producto más a productos
db.productos.insertOne({
        "timestamp": ISODate(),
        "title": "Product 11",
        "price": 3789,
        "description":"Some description for product 11",
        "code": "P11",
        "image": "Product11.com",
        "stock": 1100
    });
Listar productos con precio menor a 1000 pesos:
db.productos.find({price: {$lt: 1000}});
•	Listar los productos con precio entre los 1000 a 3000 pesos.
db.productos(find {price: {$gt: 1000, $lt: 3000 });
•	Listar los productos con precio mayor a 3000 pesos.
db.productos.find({price: {$gt: 3000}});
•	Realizar una consulta que traiga sólo el nombre del tercer producto más barato.
db.productos.find({},{title:1, _id:0}).sort({price:1}).skip(2).limit(1);
•	Hacer una actualización sobre todos los productos, agregando el campo stock a todos ellos con un valor de 100.
db.productos.updateMany({}, {$inc: {stock: 100}});
•	Cambiar el stock a cero de los productos con precios mayores a 4000 pesos.
db.productos.updateMany({price: {$gt: 4000}}, {$set: {stock: 0}});
•	Borrar los productos con precio menor a 1000 pesos
db.productos.deleteMany({price: {$lt: 1000}});
•	Creación del usuario pepe, con contraseña: asd456. Permiso solo de lectura
db.createUser({user: "pepe", pwd: "asd456", roles: [{role: "read", db: "basededatos"}]});
•	Login del usuario creado anteriormente
mongo -u pepe -p --authenticationDatabase basededatos 

``` mongo
use database
switched to db database
> db.produto.find({nome:"mouse"})
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
> db.produto.find({})
{ "_id" : 1, "nome" : "cpu i5", "qntd" : "15" }
{ "_id" : 2, "nome" : "memória ram", "qntd" : "10", "descricao" : { "armazenamento" : "8GB", "tipo" : "DDR4" } }
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({nome:"mouse"})
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
> db.produto.find({qntd:"20"})
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({qntd:"20"},{_id: 0, nome: 1})
{ "nome" : "hd externo" }
> db.produto.find({qntd:"20"},{nome: 1})
{ "_id" : 4, "nome" : "hd externo" }
> db.produto.find({qntd:{$eq: "20"}},{nome: 1})
{ "_id" : 4, "nome" : "hd externo" }
> db.produto.find({qntd:{$lte: "20"}},{nome: 1, qntd: 1})
{ "_id" : 1, "nome" : "cpu i5", "qntd" : "15" }
{ "_id" : 2, "nome" : "memória ram", "qntd" : "10" }
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20" }
> db.produto.find({qntd:{$lte: 20}},{nome: 1, qntd: 1})
> db.produto.find({qntd:{$gte: 10}},{nome: 1, qntd: 1})
> db.produto.find({qntd:{$gte: 10}})
> db.produto.find({qntd:{$gte: "10"}})
{ "_id" : 1, "nome" : "cpu i5", "qntd" : "15" }
{ "_id" : 2, "nome" : "memória ram", "qntd" : "10", "descricao" : { "armazenamento" : "8GB", "tipo" : "DDR4" } }
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({qntd:{$gte: "10"}})
> db.produto.find({qntd:{$gte: "10", $lte: "20"}})
{ "_id" : 1, "nome" : "cpu i5", "qntd" : "15" }
{ "_id" : 2, "nome" : "memória ram", "qntd" : "10", "descricao" : { "armazenamento" : "8GB", "tipo" : "DDR4" } }
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({qntd:{$gte: "15", $lte: "20"}})
{ "_id" : 1, "nome" : "cpu i5", "qntd" : "15" }
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({"descricao.conexao": "USB"})
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
{ "_id" : 4, "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({"descricao.conexao": "USB"},{_id: 0})
{ "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
{ "nome" : "hd externo", "qntd" : "20", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({"descricao.conexao": "USB"},{_id: 0, qntd: 0})
{ "nome" : "mouse", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
{ "nome" : "hd externo", "descricao" : { "conexao" : "USB", "so" : [ "Windows 10", "Windows 8", "windows 7" ] } }
> db.produto.find({"descricao.so": "windows"})
> db.produto.find({"descricao.so": "Windows"})
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
> db.produto.find({"descricao.so": {$in: ["Windows", "windows 10"]}})
{ "_id" : 3, "nome" : "mouse", "qntd" : "50", "descricao" : { "conexao" : "USB", "so" : [ "Windows", "Mac", "Linux" ] } }
```

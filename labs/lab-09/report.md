# Database Lab

## Checkpoint 1
![image](https://user-images.githubusercontent.com/84922621/162852631-5827611d-c98e-4085-843c-bdf2a1cc2fb3.png)

## Checkpoint 2
![image](https://user-images.githubusercontent.com/84922621/162853458-38710960-a4aa-42f7-87b9-de1c6c154282.png)
![image](https://user-images.githubusercontent.com/84922621/162854618-50c213d8-67cd-4382-b2a2-7c1b245d3b69.png)
![image](https://user-images.githubusercontent.com/84922621/162854853-f9f8cad8-f4cf-496e-953c-cc6cb57acd61.png)
![image](https://user-images.githubusercontent.com/84922621/162855148-92adc76e-e7ca-4612-8145-1a3272d243f1.png)

## Checkpoint 3
![image](https://user-images.githubusercontent.com/84922621/162855455-5896f53b-a42f-4f18-b622-46a990788309.png)
![image](https://user-images.githubusercontent.com/84922621/162855738-2bc73582-1917-4c1e-99a2-44c63b934c32.png)

## Checkpoint 4
1.
```
{"docs":[
{"_id":"00a271787f89c0ef2e10e88a0c0001f4","_rev":"1-c7f3ec5e61c7a461d83da2d42f64a9e4","type":"movie","title":"My Neighbour Totoro","year":1988,"director":"miyazaki","rating":8.2},
{"_id":"00a271787f89c0ef2e10e88a0c0003f0","_rev":"1-5facb9c84b721a5fe8d667c1140a54d3","type":"movie","title":"Kikis Delivery Service","year":1989,"director":"miyazaki","rating":7.8},
{"_id":"00a271787f89c0ef2e10e88a0c00048b","_rev":"1-90be3f3651b72d82da71a875e63de9c0","type":"movie","title":"Princess Mononoke","year":1997,"director":"miyazaki","rating":8.4}
],
"bookmark": "g2wAAAACaAJkAA5zdGFydGtleV9kb2NpZG0AAAAgMDBhMjcxNzg3Zjg5YzBlZjJlMTBlODhhMGMwMDA0OGJoAmQACHN0YXJ0a2V5bAAAAAFiAAAHzWpq"}
```
2.
```
$ curl -X POST admin:password@localhost:5984/hello-world/_find -d '{
>    "selector": {
>       "title": {
>          "$gt": "L"
>     }
>   }
> }' -H 'Content-Type: application/json'
{"docs":[
{"_id":"00a271787f89c0ef2e10e88a0c0001f4","_rev":"1-c7f3ec5e61c7a461d83da2d42f64a9e4","type":"movie","title":"My Neighbour Totoro","year":1988,"director":"miyazaki","rating":8.2},
{"_id":"00a271787f89c0ef2e10e88a0c00048b","_rev":"1-90be3f3651b72d82da71a875e63de9c0","type":"movie","title":"Princess Mononoke","year":1997,"director":"miyazaki","rating":8.4}
],
"bookmark": "g1AAAABweJzLYWBgYMpgSmHgKy5JLCrJTq2MT8lPzkzJBYorGBgkGpkbmluYp1lYJhukphmlGhqkWlgkGiQbGBiYWCSB9HHA9BGlIwsAfPcdnw",
"warning": "No matching index found, create an index to optimize query time."}
```
3.
```
$ curl -X POST admin:password@localhost:5984/hello-world/_index -d '{
>    "index": {
>       "fields": [
>          "title"
>       ]
>    },
>    "name": "title-json-index",
type":>    "type": "json"
> }' -H 'Content-Type: application/json'
{"result":"created","id":"_design/5e0c1e3422759aefaa2aa14ed5a8323ba33f06e3","name":"title-json-index"}
```
4.
```
$ curl -X POST admin:password@localhost:5984/hello-world/_find -d '{
>    "selector": {
>       "title": {
>          "$gt": "L"
>     }
>   }
> }' -H 'Content-Type: application/json'
{"docs":[
{"_id":"00a271787f89c0ef2e10e88a0c0001f4","_rev":"1-c7f3ec5e61c7a461d83da2d42f64a9e4","type":"movie","title":"My Neighbour Totoro","year":1988,"director":"miyazaki","rating":8.2},
{"_id":"00a271787f89c0ef2e10e88a0c00048b","_rev":"1-90be3f3651b72d82da71a875e63de9c0","type":"movie","title":"Princess Mononoke","year":1997,"director":"miyazaki","rating":8.4}
],
"bookmark": "g1AAAABneJzLYWBgYMpgSmHgKy5JLCrJTq2MT8lPzkzJBYorGBgkGpkbmluYp1lYJhukphmlGhqkWlgkGiQbGBiYWCSB9HHA9OUAdTCCtAkGFGXmJacWFyv45ucBYXZqVhYAgz0cvw"}
```

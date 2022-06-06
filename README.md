# testovacia

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### server start 

json-server data.json --routes routes.json


Poznámky ku appke: 

Zo zadania som si vybral vytvorenie appky vo Vue, pretože vnej pracujem, samozrejme by som to zvládol aj v Angulari, ale trvalo by mi to dlhšie
Appku som urobil za cca 5-6 hodín

-na spracovávanie http requestov som vytvoril mocked API pomocou JSON serveru
-design som prispôsobil na maximálnu šírku 990px, ako bolo v zadaní
-pridal som aj post request na pridávanie customerov, avšak keďže som použil mocked API bez databázy,kde by som ukladal logá, tak nemám kam ukladať loga customerov, tak pri každom novom customerovi sa nahrá obrázok od brand enterprise, ale ponechal som v konzoli console log nato, že keď pridáte obrázok, tak sa vypíšu jeho dáta.
-formulár na pridávanie customerov nieje responzívny, ani nijak extrémne nadizajnovaný, pridal som ho tam len na ukážku, že viem pracovať s http requestami
-appku som urobil responzívnu
-pridal som aj filter na hľadanie customerov

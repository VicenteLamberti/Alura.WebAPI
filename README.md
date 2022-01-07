# Alura.WebAPI
Curso Alura - Aplicação MVC para WebAPI

Este projeto irá transformar uma aplicação padrão MVC, para uma WebAPI REST. Dessa forma ela poderá ser intregrada com outras aplicações.

No padrão MVC, o retorno das informações são em VIEWS, que são páginas HTML. <Mas para ser um API é necessário retornar as informações em outros formatos para poder ser integrado.
Como por exemplo Json.

Caso um método retorne algum objeto, por padrão o retorno será em Json, porém fazer isso em uma aplicação MVC é preciso tomar alguns cuidados. Pois caso o Id que seja passado na URL, não exista a requisição será feita, mas não haverá um retorno.

Para padronizar as Actions que serão da API, ou seja, onde os retornos serão Json, é uma boa prática criar novas Controllers com esses novos métodos.

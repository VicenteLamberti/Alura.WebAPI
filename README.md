# Alura.WebAPI
Curso Alura - Aplicação MVC para WebAPI (C#)

Este projeto irá transformar uma aplicação padrão MVC, para uma WebAPI REST. Dessa forma ela poderá ser intregrada com outras aplicações.

No padrão MVC, o retorno das informações são em VIEWS, que são páginas HTML. <Mas para ser um API é necessário retornar as informações em outros formatos para poder ser integrado.
Como por exemplo Json.

Caso um método retorne algum objeto, por padrão o retorno será em Json, porém fazer isso em uma aplicação MVC é preciso tomar alguns cuidados. Pois caso o Id que seja passado na URL, não exista a requisição será feita, mas não haverá um retorno.

Para padronizar as Actions que serão da API, ou seja, onde os retornos serão Json, é uma boa prática criar novas Controllers com esses novos métodos.

Em uma aplicação MVC, os métodos retonam uma View (HTML). Exemplo, depois de inserir um objeto no banco de dados, geralmente á página é redirecionada para a página principal.

Na API o retorno são objetos Json ou então status code, dizendo se aquela operação foi um sucesso ou não.

Na API métodos que retornam objetos, caso ocorra algum problema, o retorno é o status code 404 (Not Found).

Na API métodos de inserção, retornam o status code 200 (Ok). Porém é possível ( e uma boa prática, retornar o status code 201, que comunica que foi realmente criado)
O método é o Created(). Que precisa de alguns parâmetros, como a URL do novo objeto inserido, e o próprio objeto.
  Exemplo:  
  public IActionResult Incluir(LivroUpload model)
  {
      if (ModelState.IsValid)
      {
          var livro = model.ToLivro();
          _repo.Incluir(livro);
          var uri = Url.Action("Recuperar", new { id = livro.Id });
          return Created(uri,livro);
      }
      return BadRequest();
  }

Caso ocorra o erro na inserção é retornado o status code 400 (Bad Request).

Na API no método de deleção, caso ocorra tudo certo, é retornado o código 204 (No Content) - Que diz realmente que não tem mais conteúdo apontando para aquele Id.

--Padronização

Nos métodos da API, para que não seja necessário um manual de como serão os nomes dos métodos, é usado uma convenção. Para isso é necessário utilizar os verbos Http corretos para cada tipo de requisição. Na arquitetura MVC, o padrão das rotas são Controller, Action e Id (opcional). Na API o correto é fazer as requisições pelos próprios verbos - GET, POST, PUT, DELETE. Dessa forma as rotas são Controller e Verbo.

As Controllers que serão usadas para API, não herdam de Controller, e sim de ControllerBase. Pois ela não possui suporte a Views, evitando o risco de cometer erros.

As Controllers de API devem possuir os Data Annotation [ApiController].

As Controllers de API devem possuir os Data Annotation  

Os métodos de API devem possuir os Data Annotation [Verbo] ou Verbo("{id}")], caso precisar do id na requisição.








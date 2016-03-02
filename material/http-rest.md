# Protocolo HTTP e serviços REST


O protocolo HTTP (Hypertext Transfer Protocol), como o próprio nome diz, é um protocolo de comunicação entre cliente e servidor amplamente utilizado.

Basicamente ele funciona através de Requisições (Request) por parte dos clientes e Respostas (Response) por parte do servidor.

As requisições e suas respectivas respostas segue os padrões definidos na (RFC2616)[https://tools.ietf.org/html/rfc2616].

Mais especificamente as requisições possuem o seguinte padrão:

## Linha inicial (request line)

A linha inicial é composta de três partes, separadas por espaço, que especificam a o método a ser executado, a identificação do recurso (URI) e a versão do protocolo utilizada.

Exemplo:

```http
POST http://www.minhaapi.com.br/v1/cliente HTTP/1.1
```

Basicamente o método detalha o processamento que será efetuado sobre um determinado recurso, a URI identifica o recurso alvo deste processamento e a versão do protocolo especifica a forma de computação da requisição.

## Cabeçalho (request header);

É responsável por transferir informações adicionais entre o cliente e o servidor. Uma estrutura chave-valor, opcional, especificada logo após a request line.

Exemplo:

```http
POST http://www.minhaapi.com.br/v1/cliente HTTP/1.1
Accept: application/json; charset=utf-8
Accept-Language: pt
Content-Type: application/json; charset=utf-8
```

O header basicamente detalha os metadados da request.

## Corpo da requisição (request body)

Alguns métodos do protocolo http permitem o envio de dados para o servidor através do body da requisição.

É obrigatório a inserção de uma linha em branco entre o header e o body.

Exemplo:

```http
POST http://www.minhaapi.com.br/v1/cliente HTTP/1.1
Accept: application/json; charset=utf-8
Accept-Language: pt
Content-Type: application/json; charset=utf-8
Content-Length: 39

{ "nome" : "Renan Johannsen de Paula" }
```

## Métodos (request methods)

Os métodos de uma requisição indicam a ação a ser realizada sobre um determinado recurso.

Abaixo estão listados os oito métodos suportados pelo protocolo bem como o seus respectivos objetivos:

### OPTIONS

O método **OPTIONS** consulta os métodos suportados para um determinado recurso do servidor, ou seja, retorna a lista de operações aceitas sobre um determinado recurso.

Este método é muito útil pois pode ser utilizado e explorado pelos desenvolvedores na construção de robos e na documentação de APIS.

### GET

O método **GET**, como o nome já diz, tem por objetivo a obtenção de um determinado recurso. Por exemplo, se realizarmos um GET sobre a URI **http://www.minhaapi.com.br/v1/clientes** espera-se que o servidor retorne a lista de clientes.

O método GET é considerado um método **"seguro"**, pois semanticamente esta operação serve apenas para consultas, ou seja, o recurso consultado não sofre alteração. Dado a esta característica o método GET não permite o envio de um body na requisição, pois nenhum dado será inserido ou alterado.

Sempre que entramos em web-site pelo nosso navegador o mesmo efetua uma operação de GET para a obtenção do HTML a ser exibido.

### HEAD

O método **HEAD** é uma variação do método GET onde o body da resposta não é retornada, ou seja, serve para a verificação dos cabeçalhos e do status code retornado pelo servidor. Pode ser utilizado para a validação de um determinado recurso, por exemplo, se um determinado cliente existe.
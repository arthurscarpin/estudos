## O que é uma API?

Uma **API** (Interface de Programação de Aplicações) é um conjunto de regras e definições que permite que diferentes sistemas ou programas se comuniquem entre si, sem que seja necessário conhecer os detalhes internos de funcionamento de cada um.

---

## Tipos de API

### API de Código

São funções, classes, métodos e outros recursos que uma biblioteca ou framework disponibiliza para serem usados diretamente no seu código. Exemplos: APIs do Python, Java, ou bibliotecas como React.

### API Web

É uma interface exposta por um servidor na internet, permitindo que você envie requisições (HTTP/REST, GraphQL, etc.) e receba dados como resposta. Muito utilizada para integração entre sistemas e aplicações web.

---

## Ferramentas para Testar APIs Web

Existem aplicativos que facilitam o teste, depuração e exploração de APIs Web. Eles permitem preencher campos, enviar requisições e visualizar as respostas da API de forma prática.

### Principais Ferramentas

- **Postman**  
    - Uma das ferramentas mais populares.
    - Interface amigável e intuitiva.
    - Permite salvar coleções de requisições, automatizar testes, gerar documentação e colaborar em equipe.
    - Suporta diversos protocolos: REST, GraphQL, WebSockets, entre outros.

- **Insomnia**  
    - Alternativa mais leve e direta ao Postman.
    - Foco em agilidade e simplicidade.
    - Interface limpa, com menos elementos visuais.
    - Suporte robusto para GraphQL, REST e gRPC.

Essas ferramentas são essenciais para desenvolvedores que trabalham com APIs, pois facilitam o desenvolvimento, teste e documentação das integrações.

---

## CURL
É uma ferramenta de linha de comando usada pra fazer requisições pra URLs. Suporta HTTP, HTTPS, FTP, SCP, entre vários outros protocolos. É tipo um client de API executado diretamente pelo terminal.

### Pra que serve?

- Testar APIs REST sem abrir o navegador.
- Simular chamadas GET, POST, PUT, DELETE, etc.
- Enviar headers, tokens, arquivos, etc.
- Automatizar scripts de integração.
- Fazer debug de endpoints.

### Exemplo na prática:

```bash
curl -X POST -H 'Content-Type: application/json' -d '{"postId": 1, "name": "Arthur Scarpin",  "email": "arthur@email.com.br", "body": "Meu comentário de teste"}' https://jsonplaceholder.typicode.com/comments
```

---

## Principais métodos HTTP

Os **métodos** ou **verbos** HTTP são protocolos que representam as ações realizadas ao consumir uma API Web. Eles representam qual ação você deseja fazer com um recurso.

### GET
- Serve para buscar informações.
- Não altera nada no servidor.

**Exemplo:**

`GET /users`
Busca todos os usuários

`GET /users/5`
Busca apenas o usuário com o ID: 5

### POST
- Cria algo novo.
- Envia dados para o servidor criar um novo recurso.

**Exemplo:**

`POST /users`
```json
{   
    "nome": "Arthur", 
    "idade": 25 
}
```
Cria um novo usuário

### PUT
- Atualiza um recurso inteiro.
- Envia um objeto completo e ele substitui o existente.

**Exemplo:**

`PUT /users/5`
```json
{ 
    "nome": "Juliana", 
    "idade": 30 
}
```
Atualiza todas as informaçoes do usuário de ID: 5

### `PATCH`
- Atualiza parcialmente um recurso.
- Serve pra editar só parte do recurso.

**Exemplo:**

`PATCH /users/5`
```json
{ 
    "nome": "José" 
}
```
Atualiza apenas o nome do usuário de ID: 5

### `DELETE`
- Remove o recurso.
- Apaga o recurso no servidor.

**Exemplo:**
`DELETE /users/5`
Exclui o usuário de ID: 5

---

## Outros métodos HTTP

### CONNECT
- Estabelece um túnel TCP/IP direto entre o cliente e o servidor.
- Muito usado pra conexões HTTPS via proxy.

**Exemplo:**

`CONNECT` 
`www.google.com:443 HTTP/1.1`
Quando temos um Proxy e tentamos acessar um site HTTPS.

### OPTIONS
- Retorna quais métodos HTTP um endpoint aceita.

**Exemplo:**

<u>CORS (Cross-Origin Resource Sharing)</u>
Navegadores fazem uma requisição OPTIONS antes de permitir que outro domínio bata numa API.

`OPTIONS`
`/api/users HTTP/1.1`

### HEAD
- Igual ao GET, mas sem o corpo da resposta, só contém os headers.

**Exemplo:**

`HEAD` 
`/arquivo.zip HTTP/1.1`

Checar se um recurso existe.
Ver tamanho de arquivo antes de baixar.
Fazer validação sem puxar tudo.


### TRACE
- Reenvia a requisição recebida, como um loopback.
- Serve pra debug, tipo ver se algo no meio (proxy, firewall) tá alterando a requisição.

**Exemplo:**

`TRACE`
`/ HTTP/1.1`

Pode ser explorado pra ataques tipo Cross Site Tracing (XST).
Por isso, a maioria dos servidores bloqueia esse método por padrão.

---


### Valores Read-Only
São dados que não podem ser modificados por quem consome a API.

- A API só permite ler, não escrever.
- Pode vir como uma propriedade em um JSON que não deve ser alterada, tipo um id, created_at, ou status.
Exemplo de payload com valores read-only:

```json
{
  "id": 123,
  "username": "camarada",
  "created_at": "2025-06-03T10:00:00Z"
}
```
Mesmo que o client tente mandar um PUT/PATCH com um id diferente, o servidor ignora ou rejeita.

### Safe Methods
São os métodos HTTP que não causam efeitos colaterais no servidor. Ou seja, não mudam nada no back-end.

**✅ Métodos considerados `seguros`:**
- GET 
- HEAD
- OPTIONS

**❌ Métodos não seguros `mas são úteis`:**
- POST 
- PUT
- PATCH 
- DELETE

### Métodos Idempotentes
Um método é idempotente se você pode chamar ele 1 vez ou 100 vezes com o mesmo efeito no servidor.

**✅ Métodos idempotentes:**
- GET
- PUT
- DELETE
- HEAD
- OPTIONS

**❌ Não idempotente:**
- POST
- PATCH

### Métodos Cacheáveis
Se uma resposta HTTP pode ser armazenada e reutilizada pra economizar requisições futuras, ela é cacheável. Mas depende do método HTTP e dos headers que a resposta envia.

**✅ Métodos que podem ser cacheados:**
- GET
- HEAD

**❌ Métodos não cacheáveis por padrão:**
- POST
- PUT
- PATCH
- DELETE
- OPTIONS

<u>Observações:</u>

Podem até ser cacheados em casos específicos com uso do `Cache-Control, Vary, etc...`

---

## Status de resposta
O status de resposta indica o estado de resposta da requisição seja ele positivo ou negativo.

| Código | Categoria           | Nome                      | Quando usar                                                                 |
|--------|---------------------|---------------------------|------------------------------------------------------------------------------|
| 100    | Informativo ℹ️      | Continue 🚦                | O servidor recebeu o início da requisição e o cliente pode continuar.       |
| 101    | Informativo 🔁      | Switching Protocols 🔄     | O servidor aceitou mudar de protocolo (ex: WebSockets).                     |
| 102    | Informativo ⏳      | Processing ⚙️              | Servidor está processando a requisição, mas ainda não tem resposta final.   |
| 103    | Informativo 📢      | Early Hints 🛎️            | Servidor envia dicas iniciais (ex: preload de recursos) enquanto processa. |
| 200    | Sucesso ✅           | OK 👍                      | Requisição bem-sucedida. Dados retornados com sucesso.                      |
| 201    | Sucesso 🆕          | Created 🛠️                | Novo recurso criado com sucesso.                                            |
| 202    | Sucesso ⏳          | Accepted 📬                | Pedido aceito, mas será processado mais tarde.                              |
| 204    | Sucesso 🤐          | No Content 📭              | Sucesso, mas sem conteúdo para retornar.                                    |
| 301    | Redirecionamento 🚚 | Moved Permanently 🏠       | O recurso mudou de endereço permanentemente.                                |
| 302    | Redirecionamento 🧭 | Found 🏃                   | O recurso está temporariamente em outro lugar.                              |
| 304    | Redirecionamento 🧊 | Not Modified 📦            | Nada mudou, pode usar a versão em cache.                                    |
| 400    | Erro do cliente 🤷  | Bad Request ❌             | Requisição malformada ou com dados incorretos.                              |
| 401    | Erro do cliente 🔒  | Unauthorized 🚫            | Autenticação necessária ou inválida.                                         |
| 403    | Erro do cliente 🚷  | Forbidden ⛔               | Autenticado, mas sem permissão de acesso.                                   |
| 404    | Erro do cliente 🕵️‍♂️ | Not Found ❓               | O recurso solicitado não foi encontrado.                                    |
| 405    | Erro do cliente 🙅  | Method Not Allowed 🛑      | O método HTTP usado não é permitido.                                        |
| 409    | Erro do cliente 🤼  | Conflict ⚔️                | Conflito com o estado atual do recurso.                                     |
| 422    | Erro do cliente 🧪  | Unprocessable Entity 🧯    | Dados com estrutura válida, mas conteúdo inválido.                          |
| 500    | Erro do servidor 💥 | Internal Server Error 🧨   | Algo inesperado aconteceu no servidor.                                      |
| 502    | Erro do servidor 📡 | Bad Gateway 🚧             | Servidor intermediário recebeu resposta inválida.                           |
| 503    | Erro do servidor 🛠️ | Service Unavailable 💤     | Servidor indisponível (ex: manutenção).                                     |
| 504    | Erro do servidor ⏱️ | Gateway Timeout 🕰️        | Timeout esperando outro servidor responder.                                 |

---

## Headers

São linhas no começo da requisição ou resposta HTTP que carregam informações extras. São importantes, pois o corpo `body` é só a parte visível, mas os cabeçalhos dizem o como e quem da comunicação. tipo: `dados que estamos enviando, autenticação, cache, controle de conexão e etc.`

**Exemplos com os cabeçalhos principais:**

| Cabeçalho       | Onde aparece     | Pra que serve                                                   |
| --------------- | ---------------- | --------------------------------------------------------------- |
| `Content-Type`  | Request/Response | 📦 Diz o tipo do conteúdo (`application/json`, `text/html`, etc).  |
| `Authorization` | Request          | 🔐 Passa token, API key, credenciais.                              |
| `Accept`        | Request          | 📥 Diz qual tipo de dado o cliente quer receber.                   |
| `Cache-Control` | Request/Response | 🗃️ Controla cache (tempo, se pode ou não guardar).                 |
| `ETag`          | Response         | 🆔 Identificador único da versão do recurso (ajuda no cache).      |
| `If-None-Match` | Request          | 🔄 Envia o ETag pra checar se o recurso mudou (cache condicional). |
| `User-Agent`    | Request          | 🕵️‍♂️ Info do cliente (navegador, app, etc).                          |
| `Set-Cookie`    | Response         | 🍪 Define cookies no cliente.                                      |
| `Cookie`        | Request          | 🍪 Envia cookies do cliente pro servidor.                          |
| `Location`      | Response         | 📍 URL do recurso criado (ex: depois do POST).                     |
| `Retry-After`   | Response         | ⏳ Diz quanto tempo esperar antes de tentar de novo (ex: em 503).  |

---

## Cache HTTP
É um esquema pra guardar respostas de servidor no navegador ou em algum lugar intermediário pra não ter que ficar pedindo a mesma coisa toda hora. Isso ajuda a economizar banda, acelerar o site, reduzir carga no servidor.

#### Cache-Control
É o cabeçalho HTTP que controla esse comportamento do cache. Ele manda o browser ou proxy como deve agir.

**Exemplos:**
- `no-cache`: Não usa o que tá guardado sem antes validar no servidor.
- `no-store`: Não guarda nada, zero cache.
- `public`: Pode cachear em qualquer lugar, até proxy.
- `private`: Só cache no navegador do usuário, nada de proxy.
- `max-age=3600`: Guarda por 3600 segundos *1 hora*, depois tem que atualizar.
- `must-revalidate`: Quando o cache vence, tem que confirmar com o servidor antes de usar.

---

## Padrões de API

### RPC - (Legado)
RPC `Remote Procedure Call` é um padrão de arquitetura de comunicação entre sistemas onde um programa pode chamar uma função que tá rodando em outro lugar (normalmente em outro servidor), como se fosse uma função local.

**Request:**
`POST /api HTTP/1.1`
`Host: exemplo.com`
`Content-Type: application/json`

```json
{
  "jsonrpc": "2.0",
  "method": "soma",
  "params": [4, 7],
  "id": 1
}
```
- `method`: nome da função que você quer chamar (soma)
- `params`: argumentos pra função (aqui, 4 e 7)
- `id`: um identificador pra resposta (usado pra saber qual requisição essa resposta tá respondendo)

**Response:**
```json
{
  "jsonrpc": "2.0",
  "result": 11,
  "id": 1
}
```

<u>Observações:</u>

Os padrões de RPC só utilizam o verbo `POST` para todos os tipos de requisições.

#### Tipos de RPC

| Tipo     | Formato          | Transporte  | Observações                            |
| -------- | ---------------- | ----------- | -------------------------------------- |
| JSON-RPC | JSON             | HTTP        | Simples, leve, web-friendly            |
| XML-RPC  | XML              | HTTP        | Antigo, mais verboso                   |
| gRPC     | Protocol Buffers | HTTP/2      | Rápido, binário, bom pra microserviços |
| Thrift   | Binário ou JSON  | TCP ou HTTP | Do Facebook, parecido com gRPC         |
| SOAP     | XML + WS-\*      | HTTP        | Overkill hoje em dia                   |

### SOAP - (Legado)

SOAP `Simple Object Access Protocol` é um padrão de RPC baseado em XML, criado nos anos 2000. Ele define como dois sistemas trocam mensagens XML via rede, geralmente usando HTTP, mas pode rolar em SMTP, TCP, etc.
De **Simple** não tem nada. É burocrático até o talo.

**Request:**
`POST /ws HTTP/1.1`
`Host: exemplo.com`
`Content-Type: text/xml; charset=utf-8`
`SOAPAction: "getUser"`

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
                  xmlns:usr="http://exemplo.com/user">
   <soapenv:Header/>
   <soapenv:Body>
      <usr:getUser>
         <usr:userId>42</usr:userId>
      </usr:getUser>
   </soapenv:Body>
</soapenv:Envelope>
```

- `Envelope`: Tudo fica dentro dele.
- `Header (opcional)`: Metadados tipo autenticação, tokens, etc.
- `Body`: Onde a chamada da função vai.

**Response:**
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
                  xmlns:usr="http://exemplo.com/user">
   <soapenv:Body>
      <usr:getUserResponse>
         <usr:id>42</usr:id>
         <usr:name>Arthur</usr:name>
         <usr:email>arthur@exemplo.com</usr:email>
      </usr:getUserResponse>
   </soapenv:Body>
</soapenv:Envelope>
```

### REST

REST `Representational State Transfer` é um estilo arquitetural, não um protocolo. Foi proposto em 2000 por Roy Fielding na tese de doutorado dele. É a base das APIs modernas. Você pode manipular recursos usando verbo HTTP padrão `GET, POST, PUT, DELETE, etc.`

**Request:**
`POST /users HTTP/1.1`
`Content-Type: application/json`

```json
{
  "name": "Camarada",
  "email": "camarada@example.com"
}
```

- `Stateless`: cada requisição é independente. O servidor não guarda estado entre uma e outra.
- `Client-Server`: separação total entre frontend e backend.
- `Cacheable`: pode usar cache quando fizer sentido.
- `Uniform Interface`: URLs bem definidas + verbos HTTP padronizados.
- `Resources`: tudo é um recurso identificado por uma URL.

**Response:**
`201 Created`
`Location: /users/123`

```json
{
  "id": 123,
  "name": "Camarada",
  "email": "camarada@example.com"
}
```

<u>Observações:</u>

Quando uma API atende todas as específicações do padrão REST utilizamos o termo `API RESTful`.

---

### GraphQL
GraphQL é uma linguagem de consulta pra APIs criada pelo Facebook em 2012 e liberada como open source em 2015. Diferente do REST, onde o servidor decide o shape dos dados, no GraphQL é o CLIENTE que escolhe exatamente o que quer.

#### Como funciona?

1. Você faz um POST para a mesma URL sempre (tipo /graphql)
2. No body, você manda uma query (em texto ou JSON)
3. O servidor interpreta isso, executa e responde com JSON

**Request:**
`POST /graphql`
`Content-Type: application/json`

```json
{
  "query": "{
    user(id: 42) {
      name
      email
      posts {
        title
      }
    }
  }"
}
```

- `Query`: Leitura de dados (tipo GET)
- `Mutation`: Escrita de dados (tipo POST/PUT/DELETE)
- `Subscription`: Dados em tempo real (websockets)

**Response:**
```json
{
  "data": {
    "user": {
      "name": "Arthur",
      "email": "arthur@example.com",
      "posts": [
        { "title": "GraphQL é daora" }
      ]
    }
  }
}
```

### gRPC
gRPC é um framework open source criado pelo Google que permite comunicação RPC rápida e eficiente entre serviços, usando:

- Protocol Buffers `Protobuf` pra serializar os dados `binário, compacto` 
- HTTP/2 como transporte, que dá multiplexação, streams, compressão, e baixa latência

#### Como funciona?

1. Você define seus serviços e métodos num arquivo .proto `a linguagem do Protobuf`
2. A partir desse arquivo, você gera código cliente e servidor em várias linguagens `Node, Go, Java, etc`
3. O cliente chama métodos do servidor como se fossem funções locais
4. O Protobuf cuida de transformar a chamada em bytes eficientes e o HTTP/2 manda pra outro lado

**Exemplo de um arquivo `.proto`:**

```proto
syntax = "proto3";

service UserService {
  rpc GetUser (UserRequest) returns (UserResponse);
}

message UserRequest {
  int32 id = 1;
}

message UserResponse {
  int32 id = 1;
  string name = 2;
  string email = 3;
}
```

**Exemplo de chamada em `Java`:**

```java
import io.grpc.ManagedChannel;
import io.grpc.ManagedChannelBuilder;
import your.package.UserServiceGrpc;
import your.package.UserRequest;
import your.package.UserResponse;

public class GrpcClient {
    public static void main(String[] args) {
        // Cria o canal pro servidor gRPC
        ManagedChannel channel = ManagedChannelBuilder.forAddress("localhost", 50051)
                                    .usePlaintext()  // Sem SSL (inseguro, só pra dev)
                                    .build();

        // Cria o stub do cliente (blocking stub pra chamadas síncronas)
        UserServiceGrpc.UserServiceBlockingStub stub = UserServiceGrpc.newBlockingStub(channel);

        // Cria a requisição
        UserRequest request = UserRequest.newBuilder()
                              .setId(42)
                              .build();

        // Faz a chamada RPC
        try {
            UserResponse response = stub.getUser(request);
            System.out.println("User: " + response.getName() + ", Email: " + response.getEmail());
        } catch (Exception e) {
            System.err.println("Erro: " + e.getMessage());
        } finally {
            channel.shutdown();
        }
    }
}
```

#### ✅ Vantagens
- Comunicação super rápida, eficiente e compacta (binário)
- Código gerado automaticamente, tipado e seguro
- Suporta streaming bidirecional (ideal pra tempo real)
- Usa HTTP/2 com multiplexação, compressão e priorização
- Muito usado em microserviços, especialmente em infra grande

#### ❌ Desvantagens
- Mais complexo de configurar e debugar (não é só JSON/texto)
- Não é “web friendly” puro — navegador não fala gRPC direto (precisa proxy)
- Requer conhecimento de Protobuf e geração de código
- Debugar requisição é menos óbvio que REST/JSON

### Webhook
Um webhook é um jeito de um sistema notificar outro automaticamente quando algo acontece, via uma requisição HTTP (geralmente POST).
Diferente do modelo clássico, onde você tem que ficar dando polling ficar perguntando *tem novidade?* a toda hora, o webhook faz o servidor avisar na hora — tipo um *aviso que já chegou*.

#### Como funciona?
1. Você registra uma URL no serviço X (ex: Stripe, GitHub, etc) — essa URL é o seu webhook endpoint.
2. Quando um evento relevante rola no serviço X (ex: pagamento confirmado, push no repo), ele faz um POST na sua URL com dados do evento.
3. Seu servidor recebe a chamada e trata essa informação (atualiza banco, manda e-mail, etc).

#### Request:
```json
{
  "id": "evt_1GqIC8HYgolSBA35vJfWHD9y",
  "type": "payment_intent.succeeded",
  "data": {
    "object": {
      "id": "pi_1GqIC7HYgolSBA35qKsjslXj",
      "amount": 2000,
      "currency": "usd"
    }
  }
}
```

#### ✅ Vantagens
- Eficiente: não precisa ficar fazendo requisições repetidas.
- Reativo: você reage só quando tem evento novo.
- Simples de implementar: só cria uma rota HTTP que recebe POST.

#### ⚠️ Desafios
- Segurança: precisa validar que o webhook veio do lugar certo (assinatura, token, IP).
- Garantia de entrega: às vezes o webhook falha, aí precisa retry ou lógica de idempotência.
- Debug: difícil debugar porque é “push” de eventos, não uma chamada direta sua.

#### 💡 Onde é usado?
- Pagamentos `Stripe, PayPal`
- Repositórios `GitHub, GitLab`
- Chatbots `Telegram, Slack`
- Monitoramento e alertas

---

## Modelagem de API

### Query Parameters
Query parameters são componentes da URL usados para enviar dados adicionais ao servidor em uma requisição HTTP, geralmente do tipo GET. Eles aparecem após o símbolo de interrogação `?` na URL e são formados por pares `chave-valor`, separados por `&`.

**Exemplo:**

`https://api.exemplo.com/usuarios?idade=30&cidade=SãoPaulo`

| **Característica**       | **Descrição**                                                                  |
| ------------------------ | ------------------------------------------------------------------------------ |
| **Localização**          | Após o `?` na URL e separados por `&` (ex: `...?chave1=valor1&chave2=valor2`)  |
| **Objetivo**             | Filtragem, paginação, ordenação, busca e outras consultas                      |
| **Tipo de Requisição**   | Predominantemente em requisições `GET` (sem alterar o estado do recurso)       |
| **Estrutura**            | Pares chave-valor (ex: `nome=joao`)                                            |
| **Opcionalidade**        | Geralmente opcionais; ausência não quebra a requisição                         |
| **Visibilidade**         | Expostos na URL — visíveis em logs, histórico de navegador, etc.               |
| **Limitação de Tamanho** | Sujeitos ao limite de tamanho da URL (varia por navegador e servidor)          |
| **Idempotência**         | Operações com query parameters devem ser idempotentes (sem efeitos colaterais) |
| **Boas práticas**        | Padronização de nomes, uso de valores simples, documentação clara              |
| **Complementaridade**    | Usados junto com path parameters para compor uma URL semântica e RESTful       |

### HATEOAS

O HATEOAS `Hypermedia as the engine of application state` é um princípio avançado da arquitetura `REST` definido por Roy Fielding, que propõe que a navegação entre recursos em uma API seja orientada por hipermídia `links` retornados nas respostas do servidor.

A ideia central do HATEOAS é que o cliente não precise conhecer previamente a estrutura da API. Em vez disso, ele descobre dinamicamente as ações possíveis com base nos links informados na resposta do servidor.

**Exemplo:**
Suponha uma requisição para o recurso de um usuário:
`GET /usuarios/123`

**Response:**
```json
{
  "id": 123,
  "nome": "Arthur",
  "email": "arthur@email.com",
  "_links": {
    "self": { "href": "/usuarios/123" },
    "atualizar": { "href": "/usuarios/123", "method": "PUT" },
    "excluir": { "href": "/usuarios/123", "method": "DELETE" },
    "enderecos": { "href": "/usuarios/123/enderecos", "method": "GET" }
  }
}
```

---

### Versionamento de API
O versionamento de API é uma prática crítica para a governança de APIs em ambientes corporativos, pois permite evoluir a interface pública sem quebrar contratos existentes com consumidores.

Permitir que mudanças incompatíveis `breaking changes` sejam introduzidas sem impactar consumidores legados. Isso garante previsibilidade e estabilidade, especialmente em ambientes com múltiplos clientes `web, mobile, parceiros`.

#### Principais abordagens de versionamento:

| **Estratégia**          | **Exemplo de uso**                       | **Prós**                              | **Contras**                                 |
| ----------------------- | ---------------------------------------- | ------------------------------------- | ------------------------------------------- |
| **URI Versioning**      | `GET /v1/usuarios`                       | Simples, visível, fácil de roteamento | Viola princípio REST de identificação única |
| **Header Versioning**   | `Accept: application/vnd.api.v1+json`    | Separação limpa da versão e da URI    | Mais complexo de debugar e documentar       |
| **Query Parameter**     | `/usuarios?version=1`                    | Simples de testar                     | Não recomendado por puristas do REST        |
| **Content Negotiation** | Via `Accept` ou `Content-Type` negociado | Alinhado ao REST puro                 | Implementação mais complexa                 |

#### 📌 Boas práticas corporativas
1. Evite versões no plural: Use v1, não v1.0 ou version-one.
2. Separe versões por mudança contratual, não técnica: Nova versão só se necessário.
3. Mantenha versões antigas ativas com SLA definido.
4. Documente diferenças de versão claramente (ex: changelogs).
5. Tenha uma política formal de versionamento (ex: suporte de 12 a 24 meses para cada versão).

#### 🧩 Quando versionar?
1. Alterações de estrutura de payload (ex: remover campo obrigatório)
2. Mudança na semântica de resposta
3. Modificação de comportamento de endpoints
4. Não é necessário versionar para adições não disruptivas (ex: campos opcionais, novos endpoints).

<u>Observações</u>
Não é necessário versionar para adições não disruptivas `ex: campos opcionais, novos endpoints`.

---

### Short Polling
É quando o cliente fica perguntando pro servidor de tempos em tempos:
Tipo um cron job no navegador. Cada requisição é independente.

#### Como funciona?
1. Frontend faz requisições a cada X segundos (setInterval)
2. O servidor responde com o que tiver, ou vazio.

#### ✅ Vantagens
- Simples de implementar
- Funciona em qualquer infra HTTP

#### ❌ Desvantagens
- Latência sempre alta (espera até o próximo poll)
- Gasto de banda e CPU mesmo quando não tem nada novo
- Escala mal com muitos clientes

### Long Polling
O servidor segura a requisição aberta até ter dado novo, ou até dar timeout. Aí o cliente reconecta.

#### Como funciona?
1. Cliente manda um GET /eventos
2. O servidor não responde imediatamente
3. Quando tem update → responde
4. Cliente faz nova requisição logo após

#### ✅ Vantagens
- Simula tempo real melhor que short polling
- Menos requisições à toa

#### ❌ Desvantagens
- Precisa de infra que segure conexões abertas (thread ou async)
- Mais complexo de implementar corretamente
- Ainda não é “real real time” como WebSocket

### Server-Sent Events
Server-Sent Events `SSE` é uma tecnologia baseada em HTTP que permite ao servidor enviar dados unidirecionais em tempo real para o cliente `normalmente um navegador`, de forma contínua e eficiente, utilizando uma única conexão HTTP persistente.

Diferente do WebSocket `que é bidirecional`, o SSE mantém uma conexão aberta do servidor para o cliente, permitindo o envio de eventos sempre que necessário, sem que o cliente precise requisitar repetidamente `como em polling`.

#### Como funciona?
1. O cliente realiza uma requisição HTTP com Accept: text/event-stream
2. O servidor mantém a conexão aberta e envia mensagens no formato do protocolo SSE.
3. O navegador escuta os eventos por meio da interface EventSource.

#### Exemplo:

**Código JavaScript:**
```javascript
const source = new EventSource('/eventos');

source.onmessage = function(event) {
  	console.log('Mensagem recebida:', event.data);
};
```

**Response:**
`HTTP/1.1 200 OK`
`Content-Type: text/event-stream`
`Cache-Control: no-cache`
`Connection: keep-alive`

```json
{
	"mensagem":"Atualização disponível"
}
``` 

---

### Protocolo WebSockets

É um protocolo full-duplex sobre uma conexão TCP persistente. O cliente e servidor podem mandar mensagens um pro outro a qualquer momento, sem pedir permissão e sem ficar abrindo nova conexão. É tipo uma linha direta entre navegador e servidor.

#### Como funciona?
1. O cliente faz uma requisição HTTP normal com Upgrade: websocket
2. Se o servidor aceita, eles trocam de protocolo (HTTP → WS)
3. A partir daí, rola um canal aberto, bidirecional, até alguém encerrar

**Request:**

`GET /chat HTTP/1.1`
`Host: servidor.com`
`Upgrade: websocket`
`Connection: Upgrade`
`Sec-WebSocket-Key: dGhlIHNhbXBsZQ==`
`Sec-WebSocket-Version: 13`


**Response:**

`HTTP/1.1 101 Switching Protocols`
`Upgrade: websocket`
`Connection: Upgrade`
`Sec-WebSocket-Accept: [hash]`

Aí começa o papo em WebSocket.

#### Comunicação depois do handshake
- Mensagens vão em formato binário ou texto
- Sem cabeçalho HTTP
- Latência mínima
- Comunicação bidirecional real: servidor pode empurrar dados pro cliente sem ser solicitado

#### ✅ Vantagens
- Verdadeiro tempo real
- Comunicação bidirecional
- Menos overhead que ficar abrindo conexões HTTP
- Ideal pra: chats, games, dashboards, notificações em tempo real, sistemas de trading

#### ❌ Desvantagens
- Infra precisa aguentar conexões abertas (escala é mais difícil que REST puro)
- Nem todo proxy/load balancer curte WebSocket sem config especial
- Não tem cache, nem funciona com HTTP tradicional (sem fallback)


#### Quando usar?
| Use WebSocket se...                          | Não usar se...                        |
| -------------------------------------------- | --------------------------------- |
| Precisa de tempo real (ex: chat, game, push) | Só quer dados de tempos em tempos |
| Tem controle sobre o backend                 | Tá rodando em infra limitada      |
| Quer bidirecional de verdade                 | É só cliente → servidor           |

---

### Documentação OpenAPI

OpenAPI `antes chamado de Swagger` é uma especificação pra descrever APIs REST de forma padronizada e legível por máquina.
Você escreve ou gera um arquivo `.yaml` ou `.json` que diz:

- quais endpoints existem
- que métodos eles aceitam
- quais parâmetros esperam
- que resposta devolvem
- exemplos, schemas, validações, etc.

É tipo um manual técnico automático da tua API, que serve tanto pra humanos quanto pra máquinas.

#### Pra que serve?
- Documentar a API de forma clara
- Gerar código (cliente ou servidor)
- Validar requisições/respostas
- Testar a API via UI (Swagger UI)
- Padronizar a comunicação entre times

**Exemplo simples em YAML:**

```yaml
openapi: 3.0.0
info:
  title: API de Usuários
  version: 1.0.0

paths:
  /users:
    get:
      summary: Lista todos os usuários
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/User'

components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: integer
        name:
          type: string
```

#### Ferramentas que usam OpenAPI
- `Swagger UI`: gera uma interface visual interativa
- `Swagger Codegen / OpenAPI Generator`: gera código client/server automático
- `Postman`: importa/valida via OpenAPI
- `Redoc`: outra UI bonitona
- `VSCode plugins`: highlight, validação, autocomplete...

#### ✅ Vantagens
- Evita mal-entendidos entre front e back
- Garante contrato válido tipo uma `interface` entre os dois
- Dá pra gerar SDKs automaticamente
- Ajuda a validar testes de integração

#### ❌ Desvantagens
- Pode dar trampo manter atualizado se você faz tudo na mão
- Muito verboso pra APIs grandes `mas é possível modularizar`
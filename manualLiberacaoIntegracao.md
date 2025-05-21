# Manual de Integração

> Versão 1.0 | Atualizado em: 14/05/2025

---

## 📑 Sumário

- [Termos de Uso](#tdu)
- [Introdução](#int)

## [1. Capítulo 1: Integração](#cap1)

   - [1.1 Criando Acessos](#11-a)
   - [1.2 Buscar Acessos](#12-ba)
   - [1.3 Excluir Acessos](#13-ea)

## [2. Capítulo 2: Criar Liberação](#cap2)

   - [2.1 Criacao de Produto](#21-cp)
   - [2.2 Criação de Variedade de Produto](#22-cvp)
   - [2.3 Criação de Safra](#23-cs)
   - [2.4 Criação de Lavoura](#24-cl)
   - [2.5 Criação de Campos](#25-cc)
   - [2.6 Criação de Filial](#26-cf)
   - [2.7 Criação de Liberação](#27-ccl)

---

## ⚖️ Termos de Uso {#tdu}

Este manual, ou qualquer parte dele, **não pode** ser reproduzido, copiado, modificado ou distribuído sem autorização prévia e expressa da **Saturno Smart**. A Saturno Smart reserva‑se o direito de revisar e aprimorar seus produtos sempre que considerar necessário. Esta publicação reflete o estado do produto na **data de sua emissão** e pode não corresponder a futuras versões ou atualizações.

---

## 🧾 Introdução {#int}

Este documento tem como objetivo intruir e guiar o usuário na integração do software Ponto de Controle com ERPs e sistemas de gestão dos clientes. Assim como criação de acessos e cadastros via APIs.

## Capítulo 1: Integração {#cap1}

Para acessar a documentação de APIs do Ponto de Controle, clique na versão do software, que se encontra no canto inferior esquerdo, e em seguida, clique em documentação API.
![img](./imagens/imgIntegracao/swager.png)

### 1.1 Criando Acessos {#11-a}

Para criar um novo acesso utilize a `API POST /apiv2/access`, primeiro localize esse endpoint na documentação. Em seguida, clique na seta localizada no canto direito do bloco para expandir as opções disponíveis.

![img](./imagens/imgIntegracao/access.jpg)

Após expandir, clique no botão “Try it out” para habilitar a edição dos campos. Com os campos liberados, preencha as informações necessárias que serão enviadas ao ponto de controle. Por fim, clique em “Execute” para enviar a requisição e criar o acesso.

![img](./imagens/imgIntegracao/access2.jpg)

Para configurar corretamente a requisição, é necessário realizar algumas alterações nos campos do corpo da chamada. Primeiro, altere o campo “routeID” utilizando o ID da rota criada dentro do ponto de controle. Para localizar esse ID, acesse o menu de edição da rota no ponto de controle; ele estará visível na URL, conforme imagem de referência.

![img](./imagens/imgIntegracao/routeID.jpg)

Em seguida, atualize o campo “tag” utilizando uma TAG válida.

![img](./imagens/imgIntegracao/TAG.jpg)

Também é importante verificar o campo “repeat”, que habilita a repetição da rota quando configurado como “true”; caso deseje desabilitar essa funcionalidade, defina-o como “false”.

![img](./imagens/imgIntegracao/repeat.jpg)

No objeto “Vehicle”, altere o campo “plateNumber” para uma placa válida, conforme exemplo apresentado na imagem.

![img](./imagens/imgIntegracao/vehicle.jpg)

Após realizar todas as alterações mencionadas, clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/execute.jpg)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200.

![img](./imagens/imgIntegracao/code200.jpg)

Uma vez concluída a requisição com sucesso, o acesso será criado automaticamente na interface do pontode controle, conforme ilustrado na imagem.

![img](./imagens/imgIntegracao/acesso_criado.jpg)

### Capítulo 1.2: Buscar Acessos {#12-ba}

Para consultar os acessos criados, utilize a API GET - `/api/v2/access.`

![img](./imagens/imgIntegracao/get_access.jpg)

Para isso, clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/get_access2.jpg)

Informe o método desejado para realizar a consulta e clique em “execute”, conforme demonstrado na imagem de referência.

![img](./imagens/imgIntegracao/access_id.jpg)
**OBS:** sempre que possível, opte por realizar a busca utilizando o ID do acesso, pois essa abordagem oferece maior precisão nos resultados.

As informações da consulta serão exibidas no menu “Responses” da própria API, conforme ilustrado na imagem correspondente.

![img](./imagens/imgIntegracao/response_get.jpg)

### Capítulo 1.3: Excluir Acessos {#13-ea}

Para deletar um acesso, utilize a API DELETE - `/api/v2/acess/{accessId}`.

![img](./imagens/imgIntegracao/delete_access.jpg)

Para isso, clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/delete_access2.jpg)

Insira o ID do acesso que deseja remover e clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/execute_delete.jpg)

A resposta estará disponível no campo “Server response” e, se a operação for bem-sucedida, o servidor retornará o código 204.

![img](./imagens/imgIntegracao/response_delete.jpg)

Após a conclusão da requisição, o acesso será excluído da interface do ponto, conforme ilustrado na imagem de referência.
![img](./imagens/imgIntegracao/acesso_deletado.jpg)

## Capitulo 2: Criação de Liberação {#cap2}

Para criar uma liberação, antes é necessário criar:

- Produto
- Variedade de Produto
- Lavoura
- Safra
- Campo
- Filial

Para criar os itens citados acima, clique na versão do software, que se encontra no canto inferior esquerdo, e em seguida, clique em documentação API.
![img](./imagens/imgIntegracao/swager.png)

Na URL da documentação, altere de `http://127.0.0.1:4000/api/v2/docs/` para `http://127.0.0.1:4000/api/v2/docs-internal/`

**OBS:** O IP e porta da URL varia de acordo com o local de instalação do software.

### 2.1 Criação de Produto {#21-cp}

Para criar um produto, acesse a API POST - `/api/v2/product` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criacao_produto.png)

Preencha os campos conforme a necessidade e clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/criacao_produto2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações do produto criado, incluindo o ID que será usado para criar a liberação.

![img](./imagens/imgIntegracao/response_product.png)

### 2.2 Criação de Variedade de Produto {#22-cvp}

Para criar uma variedade de produto, acesse a API PUT - `/api/v2/product/{productId}/variety` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criacao_variedade.png)

Preencha os campos conforme a necessidade e clique em “execute” para enviar a requisição. O campo "productID" deve ser preenchido com o ID do produto criado anteriormente.

![img](./imagens/imgIntegracao/criacao_variedade2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações da variedade de produto criada, incluindo o ID que será usado para criar a liberação.

![img](./imagens/imgIntegracao/response_variedade.png)

### 2.3 Criação de Safra {#23-cs}

Para criar uma safra, acesse a API POST - `/api/v2/harvest` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criando_safra.png)

Preencha os campos conforme a necessidade e clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/criando_safra2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações da safra criada, incluindo o ID que será usado para criar a liberação.

![img](./imagens/imgIntegracao/response_safra.png)

### 2.4 Criação de Lavoura {#24-cl}

Para criar uma lavoura, acesse a API POST - `/api/v2/tillage` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criacao_lavoura.png)

Preencha os campos conforme a necessidade e clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/criacao_lavoura2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações da safra criada, incluindo o ID que será usado para criar a liberação.

![img](./imagens/imgIntegracao/response_lavoura.png)

### 2.5 Criação de Campo {#25-cc}

Para criar um campo, acesse a API POST - `/api/v2/field` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criacao_campo.png)

Preencha os campos conforme a necessidade e clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/criacao_campo2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações do campo criado, incluindo o ID que será usado para criar a liberação.

![img](./imagens/imgIntegracao/response_campo.png)

### 2.6 Criação de Filial {#26-cf}

Para criar uma filial, acesse a API POST - `/api/v2/company` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criacao_filial.png)

Preencha os campos conforme a necessidade e clique em “execute” para enviar a requisição.

![img](./imagens/imgIntegracao/criacao_filial2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações da filial criada, incluindo o ID que será usado para criar a liberação.

![img](./imagens/imgIntegracao/response_filial.png)

### 2.7 Criação de Liberação {#27-ccl}

Para criar uma liberação, acesse a API POST - `/api/v2/gather-module` e clique na seta localizada no canto direito da API e, em seguida, selecione a opção “try it out”.

![img](./imagens/imgIntegracao/criacao_liberacao.png)

Preencha os campos indicando os IDs dos produtos, variedades, safra, lavoura, campo e filial desejados e clique em “execute” para enviar a requisição. Além disso também é possível alterar as datas de início e fim da liberação, o campo "startAt" indica a data de início da liberação e o campo "endAt" indica a data de fim da liberação.

![img](./imagens/imgIntegracao/criacao_liberacao2.png)

A resposta estará disponível no campo “Server response” e, se bem-sucedida, o servidor retornará o código 200. No campo “Response Body” serão exibidas as informações da liberação criada.

![img](./imagens/imgIntegracao/response_liberacao.png)

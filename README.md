# Projeto de Testes de API com Postman - S206 Qualidade de Software

## Respostas do exercício 2:

### 1. Quantas suítes de testes você desenvolveu?
Foi desenvolvida uma única suíte de testes, agrupada na coleção Postman "TYPICODE".
Justificativa: Uma suíte de testes é um conjunto de casos de teste executados pra validar um sistema ou componente. Como todos os 6 cenários validam a mesma API (JSONPlaceholder), eles foram organizados em uma única suíte coesa.

### 2. Os testes desenvolvidos são manuais ou automatizados?
Os testes são automatizados.
Justificativa: As validações são feitas por meio de scripts em JS na aba "Scripts" do Postman. Esses scripts verificam de forma atuomatica as respostas da API (códigos de status, tamanho de arrays, conteúdo de dados), permitindo uma execução rápida e livre de erro humano.

### 3. Onde os testes se localizam na pirâmide de testes apresentada?
Localizam-se na camada intermediária da pirâmide, conhecida como Testes de Serviço (ou Testes de API).
Justificativa: Os testes operam na camada de lógica de negócio, comunicando-se diretamente com os endpoints da API. Eles não interagem com a interface do usuário (topo da pirâmide) nem testam funções de código de forma isolada (base da pirâmide).

### 4. Os testes desenvolvidos são funcionais ou não-funcionais?
São testes funcionais.
Justificativa: O foco é validar o comportamento e as funcionalidades da API: ela consegue listar posts? Ela cria um novo post corretamente? Ela retorna erro quando um post não existe? Essas são todas validações de requisitos funcionais, não de atributos não-funcionais como performance ou segurança.

### 5. Alguns dos testes desenvolvidos são testes Fim-a-Fim (End-To-End)?
Não, estes testes não são Fim-a-Fim.
Justificativa: Testes Fim-a-Fim (E2E) simulam um fluxo completo do usuário através de todas as camadas da aplicação, incluindo a UI. Os testes validam a camada de API de forma isolada, o que os classifica como testes de serviço.

### 6. O que se deve fazer para que os testes desenvolvidos funcionem em modo regressão?
Para que funcionem como testes de regressão, eles devem ser incorporados a um pipeline de (CI/CD).
Justificativa: O objetivo da regressão é garantir que novas funcionalidades não quebrem as antigas. A maneira mais eficaz de fazer isso é executar a suíte de testes automaticamente sempre que o código-fonte for alterado. Ferramentas de CI/CD (como Jenkins, GitLab CI, GitHub Actions) podem ser configuradas para rodar a coleção Postman via Newman (a versão de linha de comando do Postman), bloqueando a implantação de código defeituoso e fornecendo feedback imediato aos desenvolvedores.

Este projeto apresenta uma suíte de testes automatizados para a API pública **JSONPlaceholder (`jsonplaceholder.typicode.com`)**. A suíte foi desenvolvida com Postman para validar os endpoints de `posts` e `comments`, cumprindo os requisitos da disciplina S206 - Qualidade de Software.

## Ferramentas Utilizadas
*   **Postman:** Ferramenta para criação, execução e automação de testes de API.

## Cenários de Teste

A suíte de testes contém 6 cenários, sendo 4 positivos e 2 negativos.

### Cenários Positivos
1.  **Listar todos os Posts:** (GET) - Valida se a API retorna a lista completa com 100 posts.
2.  **Criar um Novo Post:** (POST) - Valida a criação de um novo post e a estrutura da resposta.
3.  **Atualizar um Post existente:** (PUT) - Valida a substituição completa dos dados de um post.
4.  **Consultar Comentários de um Post:** (GET) - Valida o relacionamento entre posts e comentários, verificando se os comentários retornados pertencem ao post correto.

### Cenários Negativos
5.  **Consultar um Post Inexistente:** (GET) - Valida a resposta de erro 404 ao buscar por um recurso que não existe.
6.  **Enviar um Post com Carga Útil Malformada:** (POST) - Valida que o servidor rejeita uma requisição com um corpo JSON inválido, retornando um status de erro.

## Como Executar o Projeto e Obter o Relatório

### 1. Pré-requisitos
*   Ter o [Postman](https://www.postman.com/downloads/) instalado.

### 2. Importar a Coleção
*   Clone ou baixe este repositório.
*   No Postman, clique em **"Import"** no canto superior esquerdo.
*   Selecione o arquivo `.postman_collection.json` deste projeto.

### 3. Executar os Testes
*   Após a importação, a coleção "TYPICODE" aparecerá na sua aba de Coleções.
*   Clique na coleção e selecione **"Run collection"**.
*   Na janela do "Runner", clique no botão azul **"Run TYPICODE"**.

### 4. Obter o Relatório de Testes
*   Ao final da execução, a tela do "Runner" exibirá os resultados detalhados de cada teste.
*   Para gerar um arquivo de relatório, clique em **"Export Results"** no canto superior direito e salve o arquivo JSON.
# Tutor Inteligente de Business Intelligence com IA Generativa

Este repositório reúne os artefatos técnicos do Trabalho de Conclusão de Curso:

**Aplicação da IA Generativa na Educação a Distância: Implementação de um Tutor Conversacional para Apoio ao Estudo de Business Intelligence**

O projeto consiste em um protótipo funcional de tutor conversacional educacional, desenvolvido para apoiar o estudo de uma disciplina de Business Intelligence em contexto de Educação a Distância (EaD).

A solução foi implementada em ambiente acadêmico controlado, utilizando Google Sites como camada de acesso, GitHub Pages como hospedagem da interface web, Google Cloud Run como backend em nuvem e Vertex AI/Gemini como serviço de geração de respostas.

---

## 1. Objetivo do projeto

O objetivo do projeto foi propor, implementar e descrever um protótipo funcional de tutor conversacional com inteligência artificial generativa para apoio ao estudo de Business Intelligence.

O tutor foi projetado para:

- responder dúvidas conceituais sobre a disciplina;
- apoiar o estudante na revisão de conteúdos;
- indicar materiais oficiais cadastrados no catálogo da disciplina;
- orientar o aluno de forma didática e objetiva;
- manter as respostas dentro do escopo dos conteúdos autorizados;
- atuar como apoio ao estudo, sem substituir professor, materiais oficiais ou avaliações formais.

---

## 2. Contexto acadêmico

O protótipo foi desenvolvido no contexto de um TCC do curso de Sistemas de Informação da Faculdade Impacta.

A implementação foi realizada em ambiente controlado/sandbox, com apoio institucional para testes. A solução não foi aplicada com estudantes reais nesta etapa.

Essa decisão foi adotada para evitar riscos de instabilidade técnica, exposição indevida de dados ou interferência em uma turma em produção.

---

## 3. Arquitetura da solução

A arquitetura foi organizada em camadas:

```text
Google Sites
   ↓
GitHub Pages
   ↓
Google Cloud Run
   ↓
Vertex AI / Gemini
   ↓
Resposta ao usuário
```
---

## 4. Por que há um backend no Cloud Run?

O navegador do usuário não se comunica diretamente com o modelo de IA.

Em vez disso, a interface web envia a pergunta para um backend hospedado no Google Cloud Run. Esse backend monta o prompt, incorpora o catálogo da disciplina e realiza a chamada ao modelo Gemini por meio do Vertex AI.

Essa separação foi adotada para:

- evitar exposição de credenciais no frontend;
- centralizar a lógica do tutor no backend;
- permitir maior controle sobre o prompt e o catálogo;
- aproximar a solução de uma arquitetura institucional mais segura;
- facilitar manutenção e evolução futura.

---

## 5. Estrutura do repositório

```text
tcc-tutor-bi/
│
├── index.html
├── server.js
├── catalogo-bi.json
├── package.json
├── package-lock.json
└── README.md
```

### Descrição dos principais arquivos

| Arquivo | Descrição |
|---|---|
| `index.html` | Interface web do tutor conversacional |
| `server.js` | Backend Node.js/Express responsável por chamar o Vertex AI |
| `catalogo-bi.json` | Catálogo estruturado da disciplina de Business Intelligence |
| `package.json` | Dependências e configuração do backend |
| `package-lock.json` | Registro das versões das dependências instaladas |
| `README.md` | Documentação técnica do projeto |

---

## 6. Funcionamento do fluxo

O fluxo de funcionamento ocorre da seguinte forma:

```text
1. O estudante acessa o Google Sites.
2. O Google Sites exibe o chat incorporado.
3. A interface do chat está hospedada no GitHub Pages.
4. O estudante digita uma pergunta ou usa um botão de intenção.
5. O frontend envia a mensagem para o backend no Cloud Run.
6. O backend carrega o catálogo da disciplina.
7. O backend monta o prompt de controle do tutor.
8. O backend chama o modelo Gemini via Vertex AI.
9. O Gemini gera a resposta.
10. O backend devolve a resposta para a interface.
11. O estudante visualiza a resposta no chat.
```

Exemplo simplificado:

```text
Aluno pergunta:
"O que é ETL?"

Frontend envia a mensagem para:
Cloud Run

Cloud Run monta o prompt com:
- pergunta do aluno;
- objetivo da interação;
- catálogo da disciplina;
- regras do tutor.

Vertex AI / Gemini gera:
- explicação didática;
- recomendação de material da disciplina, quando disponível.

O chat exibe a resposta ao aluno.
```

---

## 7. Base de conhecimento

O arquivo `catalogo-bi.json` funciona como base estruturada da disciplina.

Ele contém informações como:

- partes da disciplina;
- temas abordados;
- resumos;
- descrições;
- vídeos;
- apostilas;
- links institucionais.

O catálogo foi utilizado para limitar o escopo das respostas do tutor e reduzir a ocorrência de respostas genéricas ou desalinhadas ao conteúdo da disciplina.

---

## 8. Prompt do sistema

O comportamento do tutor é controlado por um prompt definido no backend.

O prompt orienta o tutor a:

- responder em português do Brasil;
- usar linguagem clara, didática e objetiva;
- atuar como apoio ao estudo;
- não substituir professor ou materiais oficiais;
- não criar provas, exercícios, questionários ou atividades;
- não inventar conteúdos fora da base recebida;
- utilizar somente o catálogo fornecido como referência;
- indicar materiais da disciplina quando pertinente.

As diretrizes do prompt foram baseadas em três fontes principais:

1. orientações institucionais recebidas durante o desenvolvimento do TCC;
2. análise dos materiais oficiais da disciplina de Business Intelligence;
3. literatura sobre tutores conversacionais, IA generativa, engenharia de prompt e respostas ancoradas em bases educacionais controladas.

---

## 9. Personalização adotada

A solução utiliza uma personalização leve.

Isso significa que o tutor não utiliza dados sensíveis, notas, histórico acadêmico ou perfil individual do estudante.

A adaptação das respostas ocorre a partir de sinais simples, como:

- pergunta digitada pelo usuário;
- intenção selecionada no botão;
- solicitação de material de apoio;
- tema identificado na interação.

---

## 10. Relação com RAG

O projeto não implementa uma arquitetura RAG completa.

Uma arquitetura RAG completa normalmente envolve:

- recuperação automática de documentos;
- embeddings;
- busca semântica;
- banco vetorial;
- seleção dinâmica de trechos relevantes.

Neste protótipo, foi adotada uma lógica inspirada em RAG, pois as respostas são orientadas por um catálogo estruturado e controlado da disciplina.

Como evolução futura, a solução pode ser integrada a APIs institucionais, como Google Drive API ou Google Classroom API, para buscar dinamicamente materiais no repositório da disciplina.

---

## 11. Permissões e acesso aos materiais

Os materiais indicados pelo tutor pertencem ao ambiente acadêmico da instituição.

Por isso, alguns links podem exigir autenticação com conta institucional da Faculdade Impacta.

Contas pessoais externas podem não conseguir acessar determinados vídeos, apostilas ou documentos, pois o permissionamento dos materiais permanece controlado pela instituição.

Essa restrição foi mantida intencionalmente para preservar a segurança e o acesso autorizado aos conteúdos acadêmicos.

---

## 12. Tecnologias utilizadas

- HTML
- CSS
- JavaScript
- Node.js
- Express
- Google Cloud Run
- Vertex AI
- Gemini
- GitHub Pages
- Google Sites
- JSON

---

## 13. Deploy

### Frontend

O frontend está publicado por meio do GitHub Pages.

Link do frontend:

```text
https://lesawa.github.io/tcc-tutor-bi/
```

### Backend

O backend está publicado no Google Cloud Run.

URL base do backend:

```text
https://gem-tutor-backend-20855190353.us-central1.run.app
```

Endpoint utilizado pelo frontend:

```text
POST /chat
```

Exemplo de requisição:

```json
{
  "message": "O que é ETL?",
  "objetivo": "normal"
}
```

Exemplo de resposta:

```json
{
  "reply": "ETL é o processo de extração, transformação e carga de dados..."
}
```

---

## 14. Como executar localmente

### Pré-requisitos

- Node.js instalado;
- Google Cloud CLI instalado;
- conta Google Cloud configurada;
- acesso ao projeto Google Cloud utilizado;
- permissão para uso do Vertex AI;
- autenticação local via Google Cloud CLI.

### Instalar dependências

```bash
npm install
```

### Autenticar no Google Cloud

```bash
gcloud auth application-default login
```

### Executar localmente

```bash
npm start
```

O backend será executado localmente na porta configurada no projeto.

---

## 15. Atualização do backend no Cloud Run

Quando houver alteração em arquivos como `server.js` ou `catalogo-bi.json`, é necessário publicar uma nova versão do backend no Cloud Run.

Comando utilizado:

```bash
gcloud run deploy gem-tutor-backend --region us-central1 --source .
```

Alterações apenas no `index.html` devem ser publicadas via GitHub Pages e não exigem novo deploy no Cloud Run.

---

## 16. Validação exploratória

A validação foi realizada por meio de testes exploratórios manuais em ambiente controlado.

Foram simuladas interações com perguntas relacionadas a temas da disciplina, como:

- Business Intelligence;
- ETL;
- modelagem dimensional;
- tabelas fato;
- métricas;
- SCD.

Os critérios observados foram:

- clareza da resposta;
- aderência ao catálogo da disciplina;
- manutenção do escopo;
- indicação adequada de materiais;
- coerência pedagógica;
- não criação de atividades avaliativas.

A solução não foi aplicada com estudantes reais nesta etapa.

---

## 17. Testes de contenção do prompt

Também foram realizados testes para verificar se o tutor respeitava as restrições definidas no prompt.

Exemplos de solicitações testadas:

- "Crie um questionário sobre ETL."
- "Faça uma prova sobre Business Intelligence."
- "Me dê exercícios para treinar modelagem dimensional."
- "Responda uma atividade complementar."

O comportamento esperado era que o tutor não criasse provas, questionários ou atividades, mas redirecionasse o estudante para explicações conceituais e materiais oficiais da disciplina.

---

## 18. Limitações identificadas

As principais limitações do projeto são:

- ausência de testes com estudantes reais;
- inexistência de métricas quantitativas de aprendizagem;
- uso de catálogo estruturado manualmente;
- ausência de RAG completo;
- dependência de permissionamento institucional para acesso aos materiais;
- limitações de personalização visual e técnica do Google Sites para componentes interativos.

---

## 19. Limitação do Google Sites

O Google Sites foi adequado como camada de publicação e acesso institucional, mas apresentou limitações para personalização avançada de um chatbox.

Por isso, a interface do tutor foi desenvolvida externamente em HTML, CSS e JavaScript, hospedada no GitHub Pages e incorporada ao Google Sites.

Essa decisão permitiu maior controle sobre o layout, o comportamento da interface e a comunicação com o backend.

---

## 20. Trabalhos futuros

Como evolução futura, recomenda-se:

- aplicar testes com estudantes reais;
- coletar indicadores de uso;
- avaliar percepção de estudantes e docentes;
- integrar o tutor ao Google Drive API ou Google Classroom API;
- implementar recuperação dinâmica de documentos;
- evoluir para uma arquitetura RAG completa;
- criar painel de acompanhamento para análise de interações.

---

## 21. Links do projeto

### Interface web do tutor

```text
https://lesawa.github.io/tcc-tutor-bi/
```

### Backend no Cloud Run

```text
https://gem-tutor-backend-20855190353.us-central1.run.app
```

### Repositório do código-fonte

```text
https://github.com/Lesawa/tcc-tutor-bi
```

> Observação: links de edição do Google Sites não são incluídos neste README por se tratar de acesso interno de manutenção da página.

---

## 22. Status do projeto

Protótipo funcional implementado e validado por testes exploratórios em ambiente controlado.

O projeto encontra-se em versão acadêmica para fins de TCC, não sendo uma aplicação em produção com estudantes reais.

---

## 23. Autoria

Projeto desenvolvido como Trabalho de Conclusão de Curso por:

- Antonio Augusto
- Giuliane Nascimento
- Letícia Watanabe

Orientador:

- Prof. Me. Gilberto Alves Pereira

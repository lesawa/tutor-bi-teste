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

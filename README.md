# Tutor Inteligente para Business Intelligence com IA Generativa

## 📌 Descrição

Este projeto foi desenvolvido como Trabalho de Conclusão de Curso (TCC) com o objetivo de explorar o uso de Inteligência Artificial Generativa no apoio ao ensino a distância (EaD), aplicado à disciplina de Business Intelligence.

O sistema consiste em um tutor conversacional que orienta o aluno, responde dúvidas e recomenda conteúdos da disciplina de forma personalizada.

---

## 🎯 Objetivo

Desenvolver um protótipo funcional de tutor educacional capaz de:

- auxiliar o aluno no processo de aprendizagem
- responder dúvidas com linguagem didática
- sugerir conteúdos organizados por partes da disciplina
- integrar IA generativa ao contexto educacional

---

## 🧠 Arquitetura do Sistema

O sistema segue a seguinte arquitetura:

Usuário → Interface Web (HTML) → Backend (Node.js no Cloud Run) → Vertex AI (Gemini) → Resposta

---

## ⚙️ Tecnologias Utilizadas

- Node.js
- Express
- Google Cloud Run
- Vertex AI (Gemini)
- HTML, CSS e JavaScript

---

## 🚀 Funcionamento

O usuário interage com o tutor por meio de uma interface web, podendo:

- fazer perguntas livres
- escolher objetivos de aprendizagem (começar, revisar, praticar, vídeo)

O backend processa a solicitação e utiliza o modelo Gemini para gerar respostas com base em um catálogo estruturado da disciplina.

---

## 📚 Base de Conhecimento

O sistema utiliza um catálogo estruturado (`catalogo-bi.json`) contendo:

- organização por partes da disciplina
- temas abordados
- materiais de apoio (apostilas e vídeos)

---

## 🔒 Acesso aos Materiais

Os materiais recomendados podem exigir autenticação institucional para acesso, pois pertencem ao ambiente acadêmico da faculdade.

---

## 🌐 Deploy

O backend foi implantado no Google Cloud Run, permitindo acesso externo e escalabilidade.

---

## 📌 Considerações Finais

Este projeto demonstra a aplicação prática de IA generativa na educação, com foco na personalização do aprendizado e integração com ambientes virtuais de ensino.

Como evolução futura, o sistema pode incorporar mecanismos de recuperação dinâmica de conteúdo (RAG) a partir de repositórios institucionais.

---
## 🔗 Demonstração

Frontend: (https://sites.google.com/d/1Yr-3pKiHs1X-wDjd6_gnld37pfD1IeMu/p/1J6UD8E4SPZY6UcrAeKF59VUC4RdN2krx/edit) 
Backend: https://gem-tutor-backend-20855190353.us-central1.run.app

---
## 🧠 Arquitetura

Usuário → Interface Web → Cloud Run → Vertex AI → Resposta

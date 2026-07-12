# 🏛️ Ateliê Generativo: Arquitetura Modernista de Brasília

Este repositório contém os artefatos, códigos e documentação referentes ao projeto final da disciplina de **Modelos Multimodais** do curso de Engenharia de Inteligência Artificial do CEUB. 

O objetivo central do projeto foi sistematizar e documentar a especialização de um modelo de Inteligência Artificial para a geração de imagens fotorrealistas da arquitetura modernista de Brasília, utilizando técnicas de *Fine-Tuning*.

**Autor:** Homério Parreira da Silva Júnior  
**Ano:** 2026  

---

## 🎯 Objetivo e Metodologia

O projeto aplicou a técnica **LoRA (Low-Rank Adaptation)** sobre o modelo pré-treinado `stable-diffusion-v1-5`. A parametrização final escolhida (Rank 16, 1500 passos, Learning Rate 2e-4) apresentou o melhor equilíbrio para consolidar os detalhes visuais icônicos de Brasília, como o uso de concreto aparente, curvas características e o céu azul do cerrado, evitando instabilidades no treinamento.

## 📊 Dataset e Curadoria

O dataset foi construído de forma 100% autoral, composto por **40 imagens originais** de construções icônicas de Brasília (Congresso Nacional, Palácio do Planalto, Museu Nacional, etc.).

* **Rotulagem Automática:** Utilizou-se o modelo `BlipProcessor` para a extração inicial de legendas.
* **Revisão Humana:** As legendas foram revisadas e corrigidas manualmente para garantir a correspondência semântica exata com as características arquitetônicas.
* **Hugging Face:** O dataset encontra-se estruturado e versionado no hub (`homerio/atelie_estilo_brasilia`).

## 📈 Avaliação e Métricas

O desempenho do modelo foi submetido a avaliações quantitativas e qualitativas:

* **CLIPScore:** Mede a similaridade de cosseno entre os *embeddings* de imagem e texto no espaço latente. 
    * *Modelo Base:* 29.88
    * *Modelo com LoRA:* **34.31** (Comprovando a eficácia da especialização semântica).
* **Avaliação Humana:** Realizada por meio de formulários estruturados em grade comparativa.
* **Teste de Memorização (Overfitting):** Testes específicos foram aplicados para garantir que o modelo aprendeu a generalizar o conceito de "modernismo", em vez de apenas reproduzir cópias exatas das imagens de treino.

## ⚖️ Análise Crítica: Ética e Legislação

Conforme detalhado no relatório do projeto, o desenvolvimento deste modelo considerou rigorosamente o marco legal brasileiro:
* **Direitos Autorais (Lei nº 9.610/1998):** A curadoria do dataset para fins acadêmicos e o *data mining* respeitam os preceitos legais. A equipe detém os direitos sobre o código e parametrizações, embora as imagens geradas pela IA por processos estocásticos não possuam autoria humana direta pixel a pixel.
* **LGPD:** O conjunto de treinamento focou exclusivamente em fachadas arquitetônicas urbanas. Não houve processamento, coleta ou armazenamento de dados pessoais sensíveis (rostos, placas de veículos, etc.), isentando o projeto de infrações de privacidade.

---

## 🚀 Como Usar (Quickstart)

Você pode reproduzir a geração de imagens utilizando a biblioteca `diffusers`. O adaptador LoRA está hospedado no Hugging Face sob o ID `homerio/estilo_arquitetura_modernista_brasilia_v4`.

O notebook pronto para gerar o app gradio esta disponível em: 
https://www.kaggle.com/code/homeriojr/04-pipeline-gradio-kaggle-ipynb

### Pré-requisitos
```bash
pip install -q --upgrade diffusers transformers accelerate peft

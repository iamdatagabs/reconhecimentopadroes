# Reconhecimento de Padrões
## Estudo acadêmico de redes siamesas com transferência de aprendizado

Repositório dedicado ao registro de uma atividade desenvolvida no contexto da disciplina de **Reconhecimento de Padrões**. O trabalho explora redes siamesas para comparar imagens e aprender relações de similaridade entre amostras.

[![Abrir no Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/iamdatagabs/reconhecimentopadroes/blob/main/SiameseComRedePreTreinada.ipynb)

O material está organizado em um notebook experimental, com foco didático e acadêmico. Seu objetivo é documentar o processo de implementação, explicitar as escolhas metodológicas e facilitar a leitura e a reprodução dos experimentos.

---

## 1. Contextualização

Redes siamesas (*Siamese Neural Networks*) são arquiteturas compostas por ramos que compartilham pesos e processam entradas distintas para produzir representações comparáveis. Em vez de aprender somente a atribuir uma classe a uma imagem, esse tipo de modelo é treinado para estimar se duas amostras pertencem ou não à mesma categoria.

Essa formulação está relacionada ao aprendizado de métricas (*metric learning*) e permite estudar tarefas de comparação, verificação e reconhecimento com base na similaridade entre representações.

## 2. Objetivo do estudo

Implementar e explorar uma rede siamesa aplicada à comparação de imagens, observando as etapas de preparação dos dados, formação de pares, treinamento da arquitetura e avaliação do comportamento do modelo.

### Objetivos específicos

- Revisar o funcionamento geral de redes siamesas;
- Preparar imagens e organizar amostras por categoria;
- Construir pares positivos e negativos para o treinamento;
- Investigar o uso de uma rede pré-treinada como extratora de características;
- Observar os efeitos das escolhas de arquitetura e função de perda sobre o aprendizado.

## 3. Organização do repositório

| Arquivo | Descrição |
| --- | --- |
| [SiameseComRedePreTreinada.ipynb](./SiameseComRedePreTreinada.ipynb) | Notebook principal com a implementação experimental e as etapas do estudo. |

## 4. Abordagem metodológica

O notebook foi reorganizado como um roteiro acadêmico com as seguintes etapas:

1. **Preparação das imagens:** leitura, conversão para RGB e redimensionamento para 224 × 224;
2. **Separação por categoria:** classes de treinamento e avaliação são disjuntas;
3. **Construção de pares:** geração balanceada de pares positivos (mesma categoria) e negativos (categorias distintas);
4. **Codificação compartilhada:** VGG16 pré-treinado no ImageNet, sem as camadas de classificação originais e com backbone congelado;
5. **Comparação:** diferença absoluta entre embeddings e saída sigmoide para estimar similaridade;
6. **Treinamento:** lotes amostrados sob demanda e entropia cruzada binária;
7. **Testes funcionais:** verificações de dimensões, balanceamento de pares e faixa/formato das predições antes do treinamento;
8. **Avaliação:** tarefa N-way one-shot em categorias reservadas, com visualização das curvas de treinamento.

A implementação utiliza Python, TensorFlow/Keras, NumPy, Matplotlib e Pillow. O pré-processamento do VGG16 segue a especificação oficial: conversão RGB para BGR e centralização por canal, sem divisão por 255 ([documentação TensorFlow](https://www.tensorflow.org/api_docs/python/tf/keras/applications/vgg16/preprocess_input)).

## 5. Dados e execução

O notebook foi originalmente preparado para execução no **Google Colab** e faz referência à base de imagens **Fruits-360**. A versão atual do código espera encontrar os dados em um diretório do Google Drive:

`/content/drive/MyDrive/data/fruits-360/Training`

Esse é o valor inicial de `BASE_DIR` no notebook. Ajuste-o conforme a localização da pasta `Training` no seu Google Drive. A base de imagens não está armazenada neste repositório.

### Para reproduzir o experimento

1. Abra o notebook no Google Colab ou em um ambiente Jupyter com suporte às dependências;
2. Disponibilize a base Fruits-360 e confira a organização das pastas por categoria;
3. Atualize `BASE_DIR` na seção de configuração;
4. Confira `SAMPLES_PER_CLASS`, `TRAIN_CLASS_FRACTION`, `BATCH_SIZE`, `EPOCHS` e `N_WAY`;
5. Execute as células em sequência e registre versões das bibliotecas, configurações e resultados obtidos.

> **Nota de reprodutibilidade:** o notebook contém uma referência de caminho local do Google Drive e registros de execução que podem refletir o ambiente original. Portanto, a execução em outro ambiente depende da configuração dos dados e das dependências. Os resultados devem ser interpretados como parte de um exercício acadêmico, e não como evidência de desempenho validado para uso em produção.

## 6. Escopo e limitações

Este repositório documenta um exercício de natureza didática. O notebook inclui testes rápidos de integridade do gerador de pares e da saída da arquitetura. Esses testes verificam condições funcionais básicas, mas não substituem uma execução completa nem devem ser interpretados como validação científica ou benchmark. A avaliação por categorias reservadas é uma escolha didática e não substitui validação independente de hiperparâmetros. Para uma análise experimental mais robusta, seriam necessários, entre outros cuidados:

- Separação dos dados em conjuntos de treinamento, validação e teste sem vazamento de informação;
- Controle de aleatoriedade e documentação das sementes utilizadas;
- Registro das versões de software, hiperparâmetros e condições de hardware;
- Métricas apropriadas à tarefa de comparação, acompanhadas de análise dos erros;
- Comparação com métodos de referência e repetição dos experimentos.

## 7. Referência conceitual

A implementação foi adaptada de um tutorial introdutório sobre redes siamesas:

- *Siamese Networks: Line by Line Explanation for Beginners*. Towards Data Science. [Acessar o material](https://towardsdatascience.com/siamese-networks-line-by-line-explanation-for-beginners-55b8be1d2fc6).

A referência é indicada como ponto de partida conceitual; a implementação deste repositório contém adaptações descritas no próprio notebook.

## 8. Natureza acadêmica

Material desenvolvido para fins de estudo e aprendizagem na disciplina de **Reconhecimento de Padrões**. O código e a documentação devem ser compreendidos dentro desse contexto formativo.

---

**Autor:** [Gabriel Passos de Jesus](https://github.com/iamdatagabs)  
**Repositório:** [github.com/iamdatagabs/reconhecimentopadroes](https://github.com/iamdatagabs/reconhecimentopadroes)  
**Portfólio:** [iamdatagabs.github.io/iamdatagabs/portfolio](https://iamdatagabs.github.io/iamdatagabs/portfolio/)

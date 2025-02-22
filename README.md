# 🚀 Detecção de Objetos com YOLOv4 e Darknet 🎯

Este projeto tem como objetivo demonstrar a configuração e utilização do YOLO (You Only Look Once) através da framework Darknet para detecção de objetos em imagens. Desenvolvido em Google Colab com suporte a GPU, inclui etapas desde a compilação até a visualização de resultados.

![Exemplo de Detecção](predictions.jpg)

📋 **Índice**  
[🌟 Visão Geral](#-visão-geral)  
[🔧 Funcionalidades](#-funcionalidades)  
[💻 Requisitos](#-requisitos)  
[🔧 Instalação](#-instalação)  
[🚀 Uso](#-uso)  
[📂 Estrutura do Projeto](#-estrutura-do-projeto)  
[📈 Resultados Esperados](#-resultados-esperados)  
[🤝 Contribuições](#-contribuições)  
[📜 Licença](#-licença)  
[🙏 Reconhecimentos](#-reconhecimentos)  
[🌐 Links Úteis](#-links-úteis)

---

## 🌟 Visão Geral
O projeto aborda:  
✅ Configuração do ambiente com GPU no Google Colab.  
✅ Compilação da Darknet com suporte a GPU, CUDA e OpenCV.  
✅ Utilização de pesos pré-treinados do YOLOv4.  
✅ Detecção de objetos em imagens e visualização dos resultados.  

Ideal para praticar configurações avançadas e entender o fluxo de trabalho do YOLO.

---

## 🔧 Funcionalidades
- **Detecção em Tempo Real**: Processamento de imagens com YOLOv4.  
- **GPU Acceleration**: Configuração otimizada para desempenho.  
- **Métricas de Saída**: Geração de arquivo `predictions.jpg` com objetos identificados.  
- **Visualização Integrada**: Função para exibir resultados com `Matplotlib`.

---

## 💻 Requisitos
- **[Google Colab](https://colab.research.google.com/)** (ou outro ambiente com GPU compatível).  
- Bibliotecas necessárias:  
  ```bash
  tensorflow >= 2.0, opencv-python, matplotlib

## 🔧 Instalação

### 1. Clonar e Configurar a Darknet
```bash
!git clone https://github.com/AlexeyAB/darknet
#Muda o diretório para utilizar o Darknet

 `%cd darknet`
---
# Habilitar recursos avançados
!sed -i 's/OPENCV=0/OPENCV=1/' Makefile      # Ativa processamento de imagem
!sed -i 's/GPU=0/GPU=1/' Makefile            # Habilita aceleração GPU
!sed -i 's/CUDNN=0/CUDNN=1/' Makefile        # Ativa cuDNN para Deep Learning
!sed -i 's/CUDNN_HALF=0/CUDNN_HALF=1/' Makefile  # Precisão mista (performance)

# Configurar arquitetura para Tesla T4 (compute capability 7.5)
!sed -i 's/ARCH= -gencode arch=compute_60,code=sm_60/ARCH= -gencode arch=compute_75,code=sm_75/' Makefile

# Compilar o framework
!make

```bash
### 2. Baixar Pesos do YOLOv4

## 🚀 Uso
#Detecção em Imagem
```bash
!./darknet detect cfg/yolov4.cfg yolov4.weights data/giraffe.jpg

#Visualizar Resultados
```bash
import cv2
import matplotlib.pyplot as plt

def mostrar(frame):
    imagem = cv2.imread(frame)
    plt.figure(figsize=(18, 10))
    plt.axis('off')
    plt.imshow(cv2.cvtColor(imagem, cv2.COLOR_BGR2RGB))
    plt.show()

mostrar('predictions.jpg')

## 📂 Estrutura do Projeto
```bash
darknet/
├── cfg/               # Arquivos de configuração do YOLO
├── data/              # Imagens de exemplo
├── yolov4.weights     # Pesos pré-treinados
├── darknet            # Executável compilado
└── predictions.jpg    # Resultado gerado

## 📈 Resultados Esperados
Arquivo `predictions.jpg` com bounding boxes identificando objetos.

Métricas de confiança exibidas no terminal.

Gráfico interativo da imagem processada.

## 🤝 Contribuições
Contribuições são bem-vindas! Siga os passos:

Faça um fork do projeto.

Crie uma branch: `git checkout -b feature/nova-feature`.

Envie um pull request.

## 📜 Licença

Distribuído sob a licença MIT. Veja LICENSE para detalhes.

## 🙏 Reconhecimentos

AlexeyAB: Mantenedor da Darknet.

Joseph Redmon: Criador original do YOLO.

Google Colab: Plataforma de experimentação com GPU grátis.

## 🌐 Links Úteis

Documentação da Darknet

Paper YOLOv4

Tutorial Google Colab

# 🚗 **Sistema de Detecção de Placas de Veículos e Leitura de OCR**

## 📌 **Descrição**

Este projeto tem como objetivo a detecção de placas de veículos em tempo real, utilizando técnicas de **Visão Computacional**, **OCR** (Reconhecimento Óptico de Caracteres) e **Deep Learning**. O sistema captura frames de um vídeo, aplica a detecção de objetos para identificar placas de veículos, e utiliza OCR para extrair as informações das placas. As imagens são salvas em pastas específicas, e os dados sobre as placas são registrados em formato JSON.

**Tecnologias utilizadas**:
- 🚀 **YOLO** para detecção de objetos (placas)
- 🧠 **EasyOCR** para reconhecimento de caracteres
- 📦 **gRPC** para comunicação entre o cliente e o servidor
- 📸 **OpenCV** para captura e manipulação de imagens

## ⚙️ **Estrutura do Projeto**

```
📂 PROJECT_ROOT/
│  
├── assets/  
│   └── image.jpg  # Exemplo de imagem
│  
├── plates/  
│   └── plate_ABC1234.jpg  # Placas detectadas
│  
├── full_images/  
│   └── full_image_ABC1234.jpg  # Imagens completas com a placa
│  
├── server.py  # Código do servidor para detecção e processamento
├── client.py  # Código do cliente para enviar frames ao servidor
└── requirements.txt  # Dependências do projeto
```

## 📦 **Instalação**

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   ```
   
2. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

3. Garanta que você tenha os seguintes pré-requisitos:
   - Python 3.6+
   - OpenCV
   - gRPC
   - EasyOCR
   - YOLO (com modelo pré-treinado)

## 🛠️ **Como Executar**

### 1. Executando o Servidor
No servidor, inicie o gRPC e o processo de detecção de placas:

```bash
python server.py
```

O servidor ficará escutando na porta **50051** para conexões de clientes.

### 2. Executando o Cliente
O cliente envia frames para o servidor, que processa as imagens e retorna os resultados:

```bash
python client.py
```

Altere o caminho do arquivo de vídeo (`video.mp4`) ou forneça um **stream de vídeo RTSP**.

## 🔍 **Funcionalidades**

- **Detecção em tempo real**: O sistema processa frames do vídeo em tempo real, buscando placas de veículos.
- **OCR**: Após detectar a placa, o sistema utiliza o **EasyOCR** para identificar os caracteres da placa.
- **YOLO**: Utiliza um modelo **YOLO** treinado para detectar placas.
- **Armazenamento**: As imagens das placas e as imagens completas são salvas localmente nas pastas `plates/` e `full_images/`.
- **JSON**: A cada detecção de placa, os dados (como tipo de placa, caracteres, timestamp e caminho das imagens) são armazenados em um arquivo JSON para análise posterior.

## 🎨 **Personalização**

Você pode customizar o projeto de acordo com suas necessidades:

- **Modelos de detecção**: Altere o modelo YOLO ou treine um novo para melhor precisão.
- **Ajustes de OCR**: Personalize os parâmetros do **EasyOCR** para melhorar a precisão da leitura de placas.
- **Caminho do vídeo**: Modifique a origem do vídeo ou forneça um **stream RTSP** para detecção em tempo real.

## 📊 **Exemplo de Saída**

O servidor vai retornar um JSON com as informações da placa detectada:

```json
{
  "plate_characters": "ABC1234",
  "plate_type": "Tradicional",
  "plate_folder": "plates/plate_ABC1234.jpg",
  "full_image_folder": "full_images/full_image_ABC1234.jpg",
  "timestamp": "2025-03-24_15-30-45"
}
```

## 🚀 **Contribuições**

Sinta-se à vontade para contribuir com melhorias ou correções no projeto! Para isso, basta abrir uma issue ou um pull request.

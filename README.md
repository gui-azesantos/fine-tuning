# 🔥 Fine-Tuning DistilGPT-2 para Geração de Descrições de Produtos

Este projeto realiza o fine-tuning do modelo DistilGPT-2 para gerar descrições automáticas de produtos a partir de seus títulos.

## 🚀 Tecnologias Utilizadas

- 🤗 Transformers - Tokenização e modelo de linguagem.
- Datasets - Manipulação de datasets.
- PyTorch - Framework para treinamento do modelo.
- Google Colab / Jupyter Notebook - Ambiente para execução do código.

## 📂 Estrutura do Projeto

```
.
├── trn.json                 # Dataset de treinamento (JSON) [Download](https://drive.google.com/file/d/1-hXUXKPRjd020mizL3YPil-FXvxovTwR/view?usp=drive_link)
├── fine_tuning.py           # Script principal
├── README.md                # Documentação do projeto
├── results/                 # Pasta onde os modelos treinados serão salvos
```

## 📥 Instalação e Configuração

Antes de executar o projeto, instale as dependências necessárias:

```bash
pip install transformers datasets torch
```

## 📌 Como Funciona

### 1️⃣ Carregar o Dataset

O dataset JSON deve conter campos `title` e `content`:

```json
[
  {
    "title": "Smartphone Android S23",
    "content": "Celular com câmera de 50MP e 256GB de armazenamento."
  },
  {
    "title": "Fone de Ouvido Bluetooth",
    "content": "Fone sem fio com cancelamento de ruído e bateria de longa duração."
  }
]
```

### 2️⃣ Tokenização e Fine-Tuning

Os dados são processados e transformados no formato:

```
Descreva este produto: Smartphone Android S23
Descrição: Celular com câmera de 50MP e 256GB de armazenamento.
```

O modelo DistilGPT-2 é treinado para prever a descrição com base no título.

### 3️⃣ Treinamento do Modelo

O treinamento é configurado para 3 épocas com um batch size de 8:

```python
training_args = TrainingArguments(
    output_dir="./results",
    num_train_epochs=3,
    per_device_train_batch_size=8,
    learning_rate=5e-5,
    max_steps=1000
)
```

Para iniciar o treinamento, execute:

```bash
python fine_tuning.py
```

### 4️⃣ Geração de Descrição

Após o treinamento, você pode testar o modelo:

```python
descricao = gerar_descricao("Smartphone Android S23")
print(descricao)
```

## 📊 Resultados e Melhorias

✅ Modelo gera descrições coerentes e relevantes para os produtos.

🔧 Possíveis melhorias:

- Treinar com um dataset maior para melhor generalização.
- Usar modelos mais robustos (ex: GPT-3, Mistral).
- Ajustar hiperparâmetros para melhor performance.

## 📜 Licença

Este projeto está sob a licença MIT.

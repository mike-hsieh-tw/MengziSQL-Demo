# MengziSQL-Demo

This project demonstrates how to train a T5 model to translate Chinese natural language questions into SQL queries.

---

## 中文版

### 🚀 功能

*   使用 HuggingFace Transformers 微調 `Langboat/mengzi-t5-base` 模型。
*   將中文自然語言問題轉換為 SQL 查詢。
*   在 SQLite 資料庫上執行生成的 SQL 並以表格形式顯示結果。

### 📋 環境需求

*   Python 3.8+
*   `transformers`
*   `sentencepiece`
*   `datasets`
*   `accelerate`
*   `pandas`
*   `sqlite3`

### 🛠️ 操作步驟

#### 1. 安裝套件

首先，安裝所有必要的 Python 套件：

```bash
pip install transformers sentencepiece datasets accelerate pandas
```

#### 2. 準備資料庫與訓練資料

執行 `NL2SQL.ipynb` 的前幾個儲存格來：

*   建立一個名為 `sample_nl2sql.db` 的 SQLite 資料庫。
*   在資料庫中建立一個 `customers` 表格，並填入範例資料。
*   根據您的資料庫結構和問題，生成一個 `train.json` 檔案。

#### 3. 訓練模型

*   繼續執行 `NL2SQL.ipynb` 中的儲存格來載入 `Langboat/mengzi-t5-base` 模型和 tokenizer。
*   腳本會預處理 `train.json` 中的資料，將問題和資料庫結構結合起來作為模型輸入。
*   使用 `Trainer` API 來微調模型。
*   訓練完成後，模型將被儲存到 `./sql_model` 目錄下。

#### 4. 進行推論 (NL2SQL)

*   載入您剛剛在 `./sql_model` 中儲存的微調模型。
*   提供一個中文問題 (例如，「誰住台北」)。
*   模型將生成對應的 SQL 查詢。
*   腳本會執行此 SQL 查詢並顯示結果。
*   <img width="486" height="250" alt="image" src="https://github.com/user-attachments/assets/3e1f0e99-581a-40eb-9595-cd71cdb29df1" />

### 📂 檔案結構

*   `.gitignore`: Git 忽略檔案列表。
*   `NL2SQL.ipynb`: 包含所有步驟的 Jupyter Notebook，從資料準備到模型訓練和推論。
*   `sample_nl2sql.db`: (執行 Notebook 後生成) 範例 SQLite 資料庫。
*   `train.json`: (執行 Notebook 後生成) 用於模型微調的訓練資料。
*   `sql_model/`: (執行 Notebook 後生成) 儲存微調後的模型和 tokenizer。

### 🙏 致謝

本專案使用了由 Langboat 團隊開發的 [mengzi-t5-base](https://huggingface.co/Langboat/mengzi-t5-base) 模型。

---

## English Version

### 🚀 Features

*   Fine-tune the `Langboat/mengzi-t5-base` model using HuggingFace Transformers.
*   Translate Chinese natural language questions into SQL queries.
*   Execute the generated SQL on a SQLite database and display the results in a table.

### 📋 Requirements

*   Python 3.8+
*   `transformers`
*   `sentencepiece`
*   `datasets`
*   `accelerate`
*   `pandas`
*   `sqlite3`

### 🛠️ Step-by-Step Guide

#### 1. Install Dependencies

First, install all the required Python packages:

```bash
pip install transformers sentencepiece datasets accelerate pandas
```

#### 2. Prepare Database and Training Data

Run the initial cells in `NL2SQL.ipynb` to:

*   Create a SQLite database named `sample_nl2sql.db`.
*   Create a `customers` table within the database and populate it with sample data.
*   Generate a `train.json` file based on your database schema and questions.

#### 3. Train the Model

*   Continue running the cells in `NL2SQL.ipynb` to load the `Langboat/mengzi-t5-base` model and tokenizer.
*   The script will preprocess the data from `train.json`, combining the questions and database schema as input for the model.
*   Fine-tune the model using the `Trainer` API.
*   Once training is complete, the model will be saved to the `./sql_model` directory.

#### 4. Perform Inference (NL2SQL)

*   Load the fine-tuned model you just saved from `./sql_model`.
*   Provide a Chinese question (e.g., "誰住台北" ).
*   The model will generate the corresponding SQL query.
*   The script will execute this SQL query and display the results.
*   <img width="486" height="250" alt="image" src="https://github.com/user-attachments/assets/9a5eb9eb-d14d-4712-b6ae-ea08f0472924" />

### 📂 File Structure

*   `.gitignore`: A list of files for Git to ignore.
*   `NL2SQL.ipynb`: The Jupyter Notebook containing all steps, from data preparation to model training and inference.
*   `sample_nl2sql.db`: (Generated after running the notebook) The sample SQLite database.
*   `train.json`: (Generated after running the notebook) The training data for fine-tuning the model.
*   `sql_model/`: (Generated after running the notebook) Contains the fine-tuned model and tokenizer.

### 🙏 Acknowledgements

This project utilizes the [mengzi-t5-base](https://huggingface.co/Langboat/mengzi-t5-base) model developed by the Langboat team.

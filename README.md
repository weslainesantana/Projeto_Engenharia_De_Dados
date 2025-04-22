## Projeto_Engenharia_De_Dados

#### Equipe: Weslaine Santana e João Fontanella

# 🔥 Projeto de Demonstração: Apache Spark com Delta Lake e Iceberg

Este repositório apresenta um ambiente local utilizando Apache Spark (via PySpark), integrando os formatos Delta Lake e Apache Iceberg. O foco é explorar a manipulação de dados em formatos otimizados, demonstrando comandos como `INSERT`, `UPDATE` e `DELETE` em ambos os formatos.

O projeto foi estruturado seguindo boas práticas para Engenharia de Dados e inclui:
- Ambiente Python isolado com **UV**
- Notebooks Jupyter com exemplos práticos
- Tabelas simuladas com modelo ER, DDL e dados públicos
- Documentação com **MKDocs**

---

## 📦 Configuração do Ambiente

> É recomendado o uso do **UV** para garantir o isolamento e controle do ambiente.

### ✅ Instalação do ambiente com UV:
```bash
uv init
uv venv
source .venv/bin/activate
uv add pyspark==3.5.3 delta-spark==3.2.0 jupyterlab ipykernel
```

### 💡 Alternativas:
- **Com pip**:
```bash
pip install -r requirements.txt
```

- **Com poetry** (caso esteja usando `pyproject.toml`):
```bash
poetry install
```

### 📌 Ativando o ambiente:
```bash
source .venv/bin/activate
```

---

## 🧪 Execução dos Notebooks

Certifique-se de selecionar o ambiente virtual como kernel no JupyterLab:

```bash
jupyter lab
```

Os notebooks principais:
- `notebooks/spark-delta.ipynb`
- `notebooks/spark-iceberg.ipynb`

Eles contêm os exemplos de criação e manipulação de tabelas Delta e Iceberg.

---

## ⚙️ Requisitos de Sistema

- **Python 3.10 ou superior**
- **JDK 8, 11 ou 17** (não use JDK 21)
- **Apache Spark 3.5.x**
- **Ambiente Linux/Mac ou Windows com ajustes**

---

## ⚠️ Problemas Comuns e Soluções (Windows)

### Erro com `JAVA_HOME`:
> Certifique-se de que o Java está corretamente instalado e configurado.

Baixe o JDK 11:
- https://adoptium.net/temurin/releases/?version=11

Configure as variáveis de ambiente:
```powershell
$env:JAVA_HOME="C:\Program Files\Java\jdk-11"
$env:PATH="$env:JAVA_HOME\bin;$env:PATH"
```

---

### Erro: `HADOOP_HOME and hadoop.home.dir are unset`

**Causa**: Spark no Windows tenta acessar recursos do Hadoop ausentes.

### Solução:
1. Baixe o [winutils.exe](https://github.com/cdarlint/winutils) (Hadoop 2.7.1 recomendado).
2. Coloque em: `C:\hadoop\bin\winutils.exe`
3. Configure as variáveis:
```python
import os

os.environ['HADOOP_HOME'] = 'C:\\hadoop'
os.environ['PATH'] += os.pathsep + os.path.join(os.environ['HADOOP_HOME'], 'bin')
```

---

## 📊 Exemplo de Inicialização do Spark com Iceberg

```python
from pyspark.sql import SparkSession
import os

os.environ['HADOOP_HOME'] = 'C:\\hadoop'
os.environ['PATH'] += os.pathsep + os.path.join(os.environ['HADOOP_HOME'], 'bin')

spark = SparkSession.builder \
    .appName("IcebergExample") \
    .config('spark.jars.packages', 'org.apache.iceberg:iceberg-spark-runtime-3.5_2.12:1.6.1') \
    .config("spark.sql.extensions", "org.apache.iceberg.spark.extensions.IcebergSparkSessionExtensions") \
    .config("spark.sql.catalog.local", "org.apache.iceberg.spark.SparkCatalog") \
    .config("spark.sql.catalog.local.type", "hadoop") \
    .config("spark.sql.catalog.local.warehouse", "spark-warehouse/iceberg") \
    .getOrCreate()
```

---

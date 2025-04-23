## Projeto Apache Spark com Delta Lake

Projeto desenvolvido para demonstração do Apache Spark Local (pyspark) gravando arquivos no formato Delta Lake também de forma local.

Projeto python inicializado com o [UV](https://github.com/astral-sh/uv).

Comandos utilizados para setup do ambiente:

```bash copy
uv init
uv venv
source .venv/bin/activate - LINUX
.venv/scripts/activate - WINDOWS
uv add pyspark==3.5.3 delta-spark==3.2.0 jupyterlab ipykernel
```

Os exemplos de código pyspark/python para instanciar o Spark, bem como criar e manipular uma tabela Delta Lake, está no arquivo `spark-delta-lake.ipynb`.

**Nota:** Antes de executar o arquivo citado acima, não esqueça de selecionar o seu ambiente virtual (.venv) como Kernel do seu jupyter notebook.

![image](https://github.com/user-attachments/assets/9f89a471-ec02-4944-9178-3f79665f74bf)

## Projeto Apache Spark com Apache Iceberg

Projeto desenvolvido para demonstração do Apache Spark Local (pyspark) gravando arquivos no formato Apache Iceberg também de forma local.

Projeto python inicializado com o [UV](https://github.com/astral-sh/uv).

Comandos utilizados para setup do ambiente:

```bash copy
uv init
uv venv
source .venv/bin/activate - LINUX
.venv/scripts/activate - WINDOWS
uv add pyspark==3.5.3 jupyterlab ipykernel
```

Os exemplos de código pyspark/python para instanciar o Spark, bem como criar e manipular uma tabela Apache Iceberg, está no arquivo `spark-iceberg.ipynb`.

**Nota:** Antes de executar o arquivo citado acima, não esqueça de selecionar o seu ambiente virtual (.venv) como Kernel do seu jupyter notebook.

![image](https://github.com/user-attachments/assets/6394e5b6-c51e-4245-bad2-450d864e422a)
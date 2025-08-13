# 📚 Laboratório - Cluster Spark


## 🎯 Objetivo

Este é um projeto que foi estruturado para fins de estudo do `Spark` utilizando
um cluster formado pelo master e dois workers. Foi adicionado ao projeto uma
instância do `MinIO` para servir como um bucket S3 like a fim de ser utilizado
como local de armazenamento dos dados. A fim de facilitar o processo de estudo,
e interação com o Spark e com o MinIO, foi criado um `client` que inicializa um
`Jupyter Lab`.

Os `notebooks` criados pelo Jupyter Lab serão armazenados no diretório
`notebooks`. Enquanto os dados que vierem a ser armazenados no MinIO estão
mapeados para serem armazeanados no `minio_data`.


## 🚀 Inicialização

```bash
# clone do projeto
$ git clone https://github.com/alfredojoseneto/cluster_pyspark.git

# acessar o diretório do projeto
$ cd cluster_pyspark

# criar o diretório para armazenar os dados do minio
$ mkdir minio_data

# ajustar permissão em diretórios --> ATENÇÃO: isso só se aplica em ambiente para estudo! Não fazer isso em produção
$ chmod -R 777 minio_data notebooks

# buildar o pyspark-builder --> necessário porque será a base das outras imagens
$ docker build --tag builder:latest --file Dockerfile.spark-builder.yml .

# build das demais imagems
$ docker compose build

# uma vez buildado a imagem do builder:latest
$ docker compose up -d
```


## 💻 Acesso aos seviços

- Jupyter Lab: **localhost:8888**
- MinIO: **localhost:9001**
    - username: minioadmin
    - password: minioadmin
- Spark UI: **localhost:8080**

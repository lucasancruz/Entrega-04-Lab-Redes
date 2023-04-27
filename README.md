# Entrega-04-Lab-Redes
# Lucas Andrade Cruz
# Empresa: ajucloud.com.br

# Passo a passo para construir e executar o container do AjuCloud
Este documento descreve como construir e executar um container para o AjuCloud.

## Requisitos
Antes de começar, certifique-se de ter o Docker, o Dockerfile e o index.html instalados em sua máquina.
````
FROM python:3
COPY index.html /usr/src/app/ajucloud/
WORKDIR /usr/src/app/ajucloud/
EXPOSE 8000
CMD ["python3", "-m", "http.server", "8000"]
````
````
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Serviços - AjuCloud</title>
    <style>
      /* Definindo estilos CSS inline */
      body {
        font-family: Arial, sans-serif;
      }
      h1 {
        color: #2c3e50;
        font-size: 36px;
        margin-top: 50px;
      }
      h2 {
        color: #2980b9;
        font-size: 24px;
        margin-top: 40px;
      }
      p {
        color: #555;
        font-size: 16px;
        line-height: 1.5;
        margin-top: 20px;
      }
    </style>
  </head>
  <body>
    <h1>AjuCloud</h1>
    <h2>Serviços oferecidos:</h2>
    <p>
      A AjuCloud oferece serviços em nuvem de alta qualidade a preços acessíveis para empresas de todos os portes. Conheça nossos principais serviços:
    </p>
    <ul>
      <li><strong>Armazenamento em nuvem:</strong> tenha acesso aos seus arquivos de qualquer lugar e a qualquer hora, com segurança e privacidade.</li>
      <li><strong>Servidores virtuais:</strong> hospede seus sites, aplicativos e sistemas em nossos servidores virtuais, com escalabilidade e alta disponibilidade.</li>
      <li><strong>Backup em nuvem:</strong> proteja seus dados e sistemas contra perdas acidentais ou ataques cibernéticos, com backup automático em nuvem.</li>
      <li><strong>Integração com outras nuvens:</strong> integre nossos serviços com outras nuvens públicas ou privadas, para maior flexibilidade e eficiência.</li>
    </ul>
  </body>
</html>
````

## Construindo a imagem do container
1. Clone o repositório do AjuCloud.
2. Abra o terminal e navegue até o diretório raiz do repositório.
3. Execute o comando abaixo para construir a imagem do container:

````
docker build -f Dockerfile . -t servidor_ajucloud
````

## Executando o container
Execute o comando abaixo para iniciar o container:

````
docker run -d -p 460:8000 --name sistema_ajucloud servidor_ajucloud
````

## Testando o container
Para testar se a página está no ar, execute o comando:
````
wget http://127.0.0.1:460
cat index.html
````

## Parando o container
Para parar o container, execute o comando abaixo:

````
docker stop sistema_ajucloud
````

## Removendo o container
Para remover o container, execute o comando abaixo:
````
docker rm sistema_ajucloud
````

## Removendo a imagem
Para remover a imagem do container, execute o comando abaixo:
````
docker rmi servidor_ajucloud
````

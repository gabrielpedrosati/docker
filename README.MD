| Comandos | Descrição |
| ------- | --------- |
| docker run imagem | cria o container a partir da imagem e roda |
| docker run -it imagem | roda de modo interativo |
| docker run -d imagem | roda em background |
| docker run -p porta:porta imagem | habilitar a comunicação de portas entre container e pc, sendo a 1ª porta do pc e a 2ª do container |
| docker run --name app | Roda o container com um nome específico |
| docker pull imagem | baixa a imagem do Docker Hub |
| docker ps | lista containers ativos |
| docker ps -a | lista todos os containers |
| docker images | lista as imagens do sistema |
| docker image remove nome_imagem | Remove uma imagem |
| docker image tag image_id novo_nome | Cria uma nova imagem a partir de uma existente. Ex.: docker imagem tag 130d498f735a pedrosa/app:v.1.0.0  |
| docker login | login ao Docker hub |
| docker push repository/app:tagname | Sobe a imagem para o repositório |
| docker logs container | Mostra logs do container |
| docker exec container comando | Executar comandos dentro do container sem precisar acessá-lo |
| docker exec -it container comando | Executar comandos de forma interativa |
| docker stop container | Parar um container |
| docker start container | Iniciar um container parado |
| docker ps -a | Lista todos os containers |
| docker rm container | Remove um container |

## Dockerfile
- Arquivo de configuração da imagem

| Comandos | Descrição |
| --- | --- |
| FROM | É a plataforma, será rodado em Nodejs, Python, Ubuntu... |
| WORKDIR | Work Directory - pasta de trabalho |
| COPY | Copiar arquivos da máquina local para imagem |
| ADD | Copia arquivos de sites ou arquivos compactados e descompacta |
| RUN | Instalar dependências e rodar programas no terminal, executa comandos quando está criando a imagem |
| ENV | Configurações de ambiente |
| EXPOSE | Expor porta |
| USER | Usuário que vai executar a aplicação |
| CMD / ENTRYPOINT | Rodar comandos após a imagem ter sido construída |

## Versionamento de imagens
```
docker build -t nome_aplicacao:vx.x .
docker build -t app:v1.0.0 .
```

## Subindo imagem para Docker Hub
1. Criar repositório no Docker Hub

2. Construir imagem
```
docker build -t app .
```

3. Criar imagem que será armazenada no repositório com a estrutura "nome_repositorio/app:tagname".
```
docker image tag image_id usuarioteste/app:v1.0.0
```

4. Fazer login com `docker login`

5. Subindo imagem
```
docker push usuarioteste/app:v1.0.0
```

## Compartilhando imagens
Permitir compartilhar imagem sem ser pelo Docker Hub

1. Compactar a imagem
```
docker image save -o appv1.tar app:v1.0.0
```

2. Para descompactar
```
docker load -i appv1.tar
```

## Redirecionamento de Portas
Redirecionando a porta 80 do meu localhost para a porta 3000 do container

```
docker run -d -p 80:3000 --name manga app:v1.0.0
```

## Executando comandos dentro do container sem ter que entrar no container
```
docker exec nome_container ls
```

## Volumes Persistentes

Maneira de criar volumes dentro dos containers que são resistentes, se o container for excluído, o volume não será perdido.

Criar volume
```
docker volume create app-dados
```

Insepcionar o volume
```
docker volume inspecto app-dados
```

Atachar o volume a uma nova imagem
-v nome_volume:diretório_container
```
docker run -d -p 3000:3000 --name kiwi -v app-dados:/app/dados app:v2
```

## Copiando arquivos do Host -> Container e vice-versa

docker cp container:arquivo local_host

Container -> Host
```
docker cp kiwi:/app/dados/file.txt .
```

Host -> Container
```
docker cp teste.txt kiwi:/app/dados
```

## Docker Compose

Possibilidade de criar múltiplos containers que interagem entre si. Uma aplicação com múltiplos containers.

Arquivo sobre todos os containers que irão subir.

Verificando versão do docker-compose
```
docker-compose --version
```

Construir containers
```
docker-compose up
```

Para containers
```
docker-compose down
```
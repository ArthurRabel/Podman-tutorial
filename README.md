# Podman

## Instalar podman no ubuntu +20:

```bash
sudo apt install podman
```

> [!NOTE]
> Para confirmar que foi instalado corretamente verifique a versão usando: `podman --version`

## Listar imagens e containers

`podman images` Lista imagens

`podman ps` Lista containers que estão em execução

`podman ps -a` Mostra todos os containers, mesmo não estando em execução.

## Pegar uma imagem do docker hub

```bash
podman pull #NameImage
```

> [!IMPORTANT]
> Caso não de certo, verifique se o arquivo `/etc/containers/registries.conf` está correto. Este arquivo lista os registros de contêineres disponíveis e suas configurações, como endereço, autenticação, políticas de segurança, entre outros.

## Criar uma imagem de um Dockerfile

```bash
podman build #Options #Context
```
### Context

`podman build /caminho/do/contexto` O contexto refere-se aos arquivos e diretórios que ira incluir na construção da imagem. 

### Options

`podman build -t nameImage .` Aplicar um nome para imagem criação. Sem o comando o nome será gerado aleatoriamente.

`podman build -f /caminho/para/o/Dockerfile .` Especifica o arquivo ou caminho para o dockerfile.

### Exemplo

`podman build -t nameImage -f /caminho/para/Dockerfile /caminho/do/contexto`

## Criar e rodar um container

```bash
podman run #Options #NameImageOrId #Command
```

### Options

`podman run -i nameImageOrId` Interagir com o container.

`podman run -t nameImageOrId` Ver a saída do contêiner e interagir com seu terminal, mas não pode fornecer entrada interativa.

`podman run -it nameImageOrId` Permite que você interaja completamente com o terminal do contêiner.

`podman run -p 8000:8000 nameImageOrId` Mapeia respectivamente a porta do host e a porta do container.

`podman run --name nameImageOrId` Define o nome do container.

### Command

`podman run ubuntu ls /` Opcionalmente, você pode especificar um comando a ser executado dentro do contêiner no momento da inicialização. 

## Rodar um container existente

```bash
podman start #Options #NameContainerOrId
```

### Options

Mantém os mesmos options do comando `podman run`.

## Parar um container

```bash
podman stop #NameContainerOrId
``` 

## Excluir um container

```bash
podman rm #NameContainerOrId
```
> [!NOTE]
> Nessario antes parar execução do container.

## Excluir uma image

```bash
podman rmi #NameImageOrId 
```

> [!NOTE]
> Necessario antes excluir todos os containers da mesma.

## Executar um comando dentro de um container em execução

```bash
podman exec #Options #NameContainerOrId #arg...
```

### Options 

Mantém os mesmos options do comando `podman run`.

### arg

Argumentos adicionais para o comando que está sendo executado dentro do container.

`podman exec -it nameContainerOrId bash` Inicia um shell bash dentro do container.

`podman exec -it nameContainerOrId bash`


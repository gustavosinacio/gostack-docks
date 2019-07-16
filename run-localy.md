# Run Locally
1. Create Docker image:
```bash
docker build -t ghpages .
```

2. Start the container:
Ao iniciar o container é necessário mapear o **diretório raiz do projeto**, ou seja, o diretório acima de **docs** para dentro do container(project-dir):

```bash
docker run --name ghpages-cont -v project-dir/:/ghpages -p 4000:4000 ghpages
```

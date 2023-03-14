# microfrontend
Implementação de microfrontend utilizando docker

## Motivação

Inspirado no projeto [video-micro-front-end-nginx](https://github.com/mahenrique94/video-micro-front-end-nginx), esta proposta baseia-se na adoção de uma base de código desacoplada que permita uma contribuição independente e flexível.

## Requisitos
![Maintainer](https://img.shields.io/badge/docker-^4.10.0-blue)
![Maintainer](https://img.shields.io/badge/node-^19.6.0-blue)
![Maintainer](https://img.shields.io/badge/npm-^9.4.0-blue)

## Usar
Para demonstrar o desacoplamento, implementamos 4 projetos criados a partir de templates do [vitejs](https://vitejs.dev/guide/) e que são gerados durante a criação das imagens docker. Entretanto, o desacoplamento vai além: é possível clonar qualquer projeto através do git - ou mesmo uma branch - durante a geração da imagem docker e adicioná-lo ao microfrontend, como pode ser visto neste [Dockerfile](portfolio/Dockerfile).


Crie as imagens e containers docker com o comando:
``` bash
docker-compose up -d
```
Acesse no navegador  
localhost/vue  
localhost/svelte  
localhost/react  
localhost/vanilla  


## Atualizar somente um serviço
Seria oneroso se precisássemos alterar somente uma parte distinta do microfrontend e termos que, obrigatoriamente, recriar todos os containers e imagens. Nessas circunstâncias, procedemos da seguinte forma:

Execute o comando para recriar somente as imagens e os containers atualizados
```bash
docker-compose up -d --build [nomes-dos-services]
````
E, em seguida, o comando para remover as imagens em desuso
```bash
docker image prune
````

Como exemplo, você pode descomentar a linha 10 do arquivo [Dockerfile](svelte/Dockerfile) e executar os comandos anteriores. Ao acessar localhost/svelte será possível ver o texto "Vite + Svelte" ser alterado para "Welcome"
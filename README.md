# Projeto: Meu blog meu sustento

Oi. Criei este esqueleto de blog como uma forma de expor o que escrevo e também criar meios para você também o fazer. Ele está disponível gratuitamente para que você possa usar como seu blog pessoal, inclusive nada me deixaria mais feliz doque você usar como referência para criar o seu. Se você tiver alguma sugestão para melhorar ou quiser apenas bater papo, me chama no [Linkedin](https://www.linkedin.com/in/k41n3w/).

---
### Bom, mas como eu faço funcionar esse serviço?

Esse projeto esta configurado para utilizar o docker então o modo mais fácil de se colocar no ar é utilizando. Se você ainda tem conhecimento de docker recomendo esse [post](https://docs.docker.com/samples/rails/) te garanto que não vai ser um impecilho, pois com a ferramenta instalada ([Como instalar o Docker + Docker Compose](https://docs.docker.com/compose/install/)) vai ser muito mais fácil e divertido.

#### Sem mais delongas:

Faça o clone do repositorio na sua máquina e dentro da raiz do projeto, digite:
```
docker-compose build
```

Isso irá buildar a imagem do serviço na sua máquina, após a instalação terminar você vai ver uma mensagem como essa:
(...)
```
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
Done in 86.92s.
Removing intermediate container d9410a4682d7
 ---> 0d2c76d1d9d3
Step 18/18 : COPY . .
 ---> fe054aac3449
Successfully built fe054aac3449
Successfully tagged rails-bulma-blog_web:latest
```

Com isso podemos subir o serviço para construirmos o banco e arquivo master.key, para isto digite:
```
docker-compose run --rm web bash
```

Neste passo, caso você receba mensagem de erro de alguma gema, apague o arquivo `Gemfile.lock` e tente novamente.

Nesse momento temos que construir o banco e instalar as dependências do yarn antes de tentar testar o serviço no navegador.
Para construir o banco, dentro do container, digite:
```
rails db:create db:migrate 
```

Para instalar as depedências do yarn, dentro do container, digite:
```
yarn install
```

Com as configurações fetas você pode agora acessar no seu navegador o endereço http://0.0.0.0/ e ver o blog no ar! :D

---

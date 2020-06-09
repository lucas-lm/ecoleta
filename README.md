# Ecoleta :earth_asia: :earth_africa: :earth_americas:

O Ecoleta tem o obetivo de mapear pontos de coleta de resíduos que não podem ser descartados de qualquer maneira, como pilhas e lixo eletrônico.
Um ponto de coleta pode ser cadastrado pelo aplicativo web, e os dados de localização deste ponto de coleta ficam disponíveis na API pública do ecoleta.
Os pontos de coleta cadastrados podem ser visualizados através do aplicativo ecoleta, disponível para Android na Play Store.
Este projeto foi idealizado pela Rocketseat na primeira edição da Next Level Week (NLW), durante a semana do meio ambiente de 2020.

---
![](https://imgur.com/WvKt6CG.gif)
---

## Como funciona?

1. Um dono de um estabelecimento que colete resíduos especiais para descarte se cadastra na [plataforma](https://lucas-lm.github.io/ecoleta-web/).
2. Os dados sobre este estabelecimento como itens que coleta, localização, nome e endereço ficam disponíveis na nossa base de dados e pode ser acessado publicamente através da nossa API. Você pode até mesmo usar estes dados em seu próprio site/serviço/app ou criar um client personalizado :smirk:
3. Uma pessoa em busca de um local para descartar seus resíduos especiais entra no app e encontra os pontos de coleta que deseja. Por baixo dos panos o app busca os dados dos pontos de coleta na nossa API pública.
4. A partir do app a pessoa pode escolher entrar em contato com o estabelecimento escolhido ou ir até lá para fazer o descarte.
5. O estabelecimento cuida para que o descarte seja feito adequadamente e o meio ambiente agradece :seedling: :evergreen_tree: :deciduous_tree:


## API

A API do ecoleta fornece acesso a uma base de dados com informações sobre pontos de coleta de resíduos que não podem ser descartados no meio ambiente.
A URL base para acessar essas informações é https://ecoleta-279615.rj.r.appspot.com/ e os endpoints disponíveis estão todos documentados aqui abaixo.

### Experimente

Todos os endpoints da API são abertos quase todos utilizam o método GET para trazer dados da API.
Desta forma, você pode experimentar a API diretamente do seu navegador.
[Clicando aqui](https://ecoleta-279615.rj.r.appspot.com/items), por exemplo, você tem acesso aos itens que podem ser coletados. Alternativamente você também pode colar esta URL https://ecoleta-279615.rj.r.appspot.com/items diretamente no seu navegador.

### Endpoints

| Endpoint             | Método | O que ele faz?                   | O que ele retorna?                    |
| -------------------- | ------ | -------------------------------- | ------------------------------------- |
| /points              | POST   | Registra um novo ponto de coleta | -                                     |
| /points              | GET    | -                                | Todos os pontos de coleta registrados |
| /points/`<point_id>` | GET    | -                                | Um ponto de coleta específico         |
| /items               | GET    | -                                | Todos os items aceitos                |

O endpoint /points pode aceitar opcionalmente os seguintes parâmetros:

| Parâmetro | Valor                              | Exemplo      |
| --------- | ---------------------------------- | ------------ |
| city      | Nome de uma cidade                 | Taquaritinga |
| uf        | Sigla para um estado               | SP           |
| items     | IDs de items separados por vírgula | 1,2,6        |

Uma requisição para pontos de coleta que colete os items 1, 2 e 6 em Taquaritinga/SP seria:

```
https://ecoleta-279615.rj.r.appspot.com/points?city=Taquaritinga&uf=SP&items=1,2,6
```

Em caso de sucesso, o status da requisição retornado é 2xx.

Repositório: https://github.com/lucas-lm/ecoleta-api


## Aplicação Web

A aplicação web fornece uma interface gráfica amigável para registrar um novo ponto de coleta na base de dados do ecoleta.
Você pode acessar a aplicação web [clicando aqui](https://lucas-lm.github.io/ecoleta-web/), ou se preferir copiar a URL: https://lucas-lm.github.io/ecoleta-web/

### Funcionalidades

- Upload de imagem do ponto de coleta
  - Você pode escolher uma imagem para o seu ponto de coleta
  - Imagens aceitas apenas nos formatos JPG, PNG e GIF
  - Tamanho máximo da imagem de 2 MB
- Integração com mapas
  - Você pode selecionar no mapa a localização exata do seu ponto de coleta
  - Você pode 
- Geolocalização
- Opções para cidade/estado sincronizada com base de dados do IBGE

Repositório: https://github.com/lucas-lm/ecoleta-web

## App Mobile

O app mobile fornece uma interface gráfica onde é possível visualizar pontos de coleta pelo mapa.
O app está disponível para android na Play Store.

### Funcionalidades

- Visualização de detalhes dos pontos de coleta
  - Itens que o ponto de coleta aceita
  - Whatsapp
  - E-mail
  - Nome do ponto de coleta
  - Endereço do ponto de coleta
- Geolocalização
  - Abre o mapa centralizado na região em que você se encontra
  - Exibe pontos de coleta próximos de você
- Integração com mapas padrão do smartphone
  - Você pode visualizar pontos de coleta no mapa
- Integração com whatsapp
  - Você pode enviar mensagem via whatsapp para o ponto de coleta diretamente do app
- Integração com aplicativo de email
  - Você pode enviar mensagem via e-mail para o ponto de coleta diretamente do app

Repositório: https://github.com/lucas-lm/ecoleta-native

## Tecnologias utilizadas

- [NodeJS](https://nodejs.org/en/) - Interpretador de JavaScript assíncrono
- [TypeScript](https://www.typescriptlang.org/) - Um superset do javascript com tipagem estática que compila para javascript limpo
- [PostgreSQL](https://www.postgresql.org/) e [SQLite3](https://www.sqlite.org/index.html) - Bancos de dados relacionais. (SQLite é usado em ambiente de desenvolvimento e PostgreSQL em produção)
- [Express](https://expressjs.com/) - Framework web rápido, minimalista e não opinativo para NodeJS
- [AWS S3](https://aws.amazon.com/pt/s3/) - Armazenamento de arquivos. (Utilizado para armazenar as imagens enviadas)
- [ReactJS](https://reactjs.org/) - Uma biblioteca declarativa e flexível para criação de interfaces do usuário
- [React Native](https://reactnative.dev/) - Framework para construção de aplicativos nativos com React
- [Expo](https://docs.expo.io/) - Plataforma para criação de aplicativos nativos com React
- [KnexJS](http://knexjs.org/) - Um query builder flexível e portável para PostgreSQL, MySQL e SQLite3
- [Multer](https://github.com/expressjs/multer) - Um middleware para ExpressJS para o tratamento de requisições multipart/form-data
- [Axios](https://github.com/axios/axios) - Cliente HTTP baseado em Promises para o Browser e NodeJS
- [React Dropzone](https://react-dropzone.js.org/) - Um simples componente de upload de arquivos do tipo arrasta e solta com ReactJS
- [Leaflet](https://leafletjs.com/) - Uma biblioteca open-source para mapas mobile-friendly interativos
- [React leaflet](https://github.com/PaulLeCam/react-leaflet) - Componentes React para o Leaflet

## Autor

Feito com :heart: e :coffee: por:

[<img src="https://avatars3.githubusercontent.com/u/29049644?s=460&u=6fcf78abdf0e007afa9b2a31beaf686d79fa9173&v=4" width=115><br><sub>@lucas-lm</sub>](https://github.com/lucas-lm)

# SambAPI
## Começando
Para funcionar, basta seguir estes passos:
- Clonar ou baixar este repositório;
- Instalar as dependências da API: ```npm install```
- Iniciar o servidor ```node src/index.js```

---
## Conteúdo
Essa API possui nome das bandas de pagode mais famosas da atualidade.

Todas as **bandas** possuem as seguintes informações:

| Chave | Valor | 
| ----- | ----- |
| nomeBanda | String com o nome da banda |
| musicasFamosas | Vetor de objetos contendo algumas músicas famosas desta banda. |

Exemplo de json:
``` 
{
    nomeBanda: 'Pixote',
    musicasFamosas: [...]
}
```
As informações dos objetos de **musicasFamosas** são estas:
>Importante ressaltar que *musicasFamosas* está dentro de *bandas*. 

| Chave | Valor |
| ----- | ----- |
| nomeMusica | String com o nome da música |
| linkYoutube | String com o link para a música no Youtube |

Exemplo de json:

```
{
    ...
    musicasFamosas: [
        {
            nomeMusica: 'Saidera',
            linkYoutube: 'https://www.youtube.com/channel/UC7VUeIwBAc2ZtPGhzD-r2pA'
        },
        {
            nomeMusica: 'Cerveja de garrafa',
            linkYoutube: 'https://www.youtube.com/watch?v=cPjhBow3dLw'
        }
        ...
    ]
}
```

---
## Como consumir a API

Primeiro de tudo, você precisará de um cliente que faça requisições HTTP. Neste exemplo, é o Axios.

- Primeiro instale o Axios: ``` npm install axios ```

- Depois importe ele no seu código: ``` const axios = require('axios') ```


A url base é ```http://localhost:8000```

| Rota | Requisição esperada | Resposta |
| ---- | ------------------- | -------- |
| /bandas | JSON com uma chave "argumentos". Esta chave pode receber os valores 'all', o nome de uma banda ou o nome de uma música famosa. *Requisição POST* | Caso ```argumentos: 'all'```, retornará um objeto com todas as bandas. Caso ```argumentos: 'nomeBanda'```, retornará informações apenas da banda específicada. *Caso o valor de query seja inválido, retornará um JSON com a chave 'error'.* |

*As bandas são:*
>Exaltasamba, Turma do pagode, Raça negra, Pixote, Armandinho e Atitude 67

#### Requisição na prática
Voltando ao Axios, você fará uma requisição POST na rota acima:
``` axios.post('localhost:8000/bandas', { argumentos: 'all' }) ```

Este é um exemplo de requisição de todas as bandas.

Você consegue acessar a resposta da API através de uma promisse:
```
axios.post('localhost:8000/bandas', { argumentos: 'all' }).then(response => {
    // Todas as informações estão no parâmetro response
    console.log(response) // Exemplo de utilização
})
```
---

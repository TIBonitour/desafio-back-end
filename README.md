# Desafio Backend - Roteador de passeios

O objetivo do desafio é construir uma api [REST](https://pt.wikipedia.org/wiki/REST) que monta o melhor roteiro possível dado a disponibilidade e localização dos passeios. Um roteiro é composto por uma data de chegada, data de saída, quantidade de pessoas e uma lista de passeios organizados de uma forma que seja viável fazer todos os passeios escolhidos. O retorno da chamada da API a ser criada deve ser uma representação atualizada do atual estado do roteiro. Se o passeio adicionado não possuir disponibiidade dentro do período informado, deve ser retornado o erro adequado e o roteiro não deve ser modificado. O roteiro pode ser reordenado pra melhor comportar a rota. 
Os passeios devem ser organizados de forma que passeios no mesmo lugar sempre sejam feitos no mesmo dia, a unica exceção será quando não seja possível pela restrição das horas de passeio.
Todas as requisições devem ter como formato `application/json`.
Escreva a documentação que julgar necessário para que quem use a API não tenha duvidas de seu funcionamento.

A consulta de vagas disponiveis deve ser feito na api disponibilizada em `https://bonitour-test-api.herokuapp.com`:

O endpoint `https://bonitour-test-api.herokuapp.com/attractions` retorna todos os passeios disponíveis(query parameter são opcionais) no formato:

``` json
{  
	"attractions":[  
		{  
			"id":1588,  
			"name":"Balneário do Sol",  
			"duration":150,  
				"location":{  
				"lat":"-21.142472",  
				"long":"-56.405792"  
			}  
		},  
			{  
			"id":17110,  
			"name":"Eco Park - Passaporte ",  
			"duration":120,  
			"location":{  
				"lat":"-21.121163",  
				"long":"-56.385275"  
			}  
		}  
		...
	]  
}
```

É possível buscar passeios por data listando a disponibilidade de horário de cada um
`https://bonitour-test-api.herokuapp.com/attractions/1588?start_date=2019-12-06&end_date=2019-12-09`

``` json
{
    "id": 1588,
    "name": "Balneário do Sol",
    "duration": 150,
    "location": {
        "lat": "-21.142472",
        "long": "-56.405792"
    },
    "availability": [
        {
            "2019-12-06": [
                {
                    "09:00": 3
                },
                {
                    "09:30": 3
                },
                {
                    "10:00": 3
                },
                {
                    "13:00": 3
                },
                {
                    "13:30": 3
                },
                {
                    "14:00": 3
                },
                {
                    "14:30": 3
                },
                {
                    "15:00": 3
                }
            ]
        },
        {
            "2019-12-07": [
                {
                    "09:00": 3
                },
                {
                    "09:30": 3
                },
                {
                    "10:00": 3
                },
                {
                    "13:00": 3
                },
                {
                    "13:30": 3
                },
                {
                    "14:00": 3
                },
                {
                    "14:30": 3
                },
                {
                    "15:00": 3
                }
            ]
        },
        {
            "2019-12-08": [
                {
                    "09:00": 3
                },
                {
                    "09:30": 3
                },
                {
                    "10:00": 3
                },
                {
                    "13:00": 3
                },
                {
                    "13:30": 3
                },
                {
                    "14:00": 3
                },
                {
                    "14:30": 3
                },
                {
                    "15:00": 3
                }
            ]
        },
        {
            "2019-12-09": [
                {
                    "09:00": 3
                },
                {
                    "09:30": 3
                },
                {
                    "10:00": 3
                },
                {
                    "13:00": 3
                },
                {
                    "13:30": 3
                },
                {
                    "14:00": 3
                },
                {
                    "14:30": 3
                },
                {
                    "15:00": 3
                }
            ]
        }
    ]
}
```
`duration` representa o tempo de duração do passeio em minutos, quando o valor for zero significa que o passeio tem tempo de duração livre, ou seja, o cliente pode passar o tempo que ele desejar no atrativo na data especificada.

`availability` representa a lista de dias e horários (`vacancies`) com seus respectivos números de vagas disponíveis.

Bonus: 

 - Fornecer endpoint pra adição de passeio informando a data e horario (ainda devem ser respeitados as regras citadas anteriormente)
 - Possibilidade de travar horario/data de um dado atrativo.  (ainda devem ser respeitados as regras citadas anteriormente)

Não é necessário implementar autorização e autenticação. Utilize a linguagem que se sentir mais confortável, mas as seguintes são preferíveis em ordem de prioridade:  Ruby, Node, Python, Java. Utilize o banco de dados que considerar mais aplicável ao problema.

Utilize o que considera boas práticas de programação, refatoração e testes de código.
Utilize um repositório Git privado como BitBucket, Gitlab ou Github, compartilhando o código.

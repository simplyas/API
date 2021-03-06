# Localidades do Contrato

Este recurso permite gestão de localidades para organização dos recursos no sistema.

- [Lista Localidades](#lista-localidades)
- [Nova Localidade](nova-localidade)
- [Atualiza Localidade](atualiza-localidade)
- [Deleta localidade](deleta-localidade)
----
<br/>


**Lista Localidades**
----
Retorna uma lista de localidades e seus terminais.

* **URL**

  {{api-url}}/requestGroups

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | ```{"group_name":"LOCALIADADE","group_token":"3f7f681b-33b8-4595-82cc-41094a9333fc","terminals":[{"terminal_name":"TV1","terminal_token":"d24f88e6-6466-49f3-9156-58a295cb5f33","internet_address":"187.185.80.228"}]}``` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Informe um hash correto."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/requestGroups' \
  --header 'Authorization: Basic bW9kYm94XYIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}"}'
  ````

<br/>


**Nova Localidade**
----
 Recebe requisição contendo a hash do contrato e propriedades para cadastrar nova localidade.

* **URL**

  {{api-url}}/submitGroup

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| name | Obrigatório | Identificação da localidade com no mínimo 3 e máximo 30 caracteres |
	| terminals | Opcional | ``["d24f88e6-6466-49f3-9156-58a295cb5f33"]`` |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Localidade criada com sucesso!","group_token":"d24f88e6-6466-49f3-9156-58a295cb5f33"}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Informe o label com 3 a 30 caracteres."}` |
	| 409 | `{"error":"Existe outra localidade com o mesmo nome. Escolha um nome diferente."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/submitGroup' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","name":"{{name}}","terminals":"{{terminals}}","language":"{{language}}"}'
  ````

<br/>

**Atualiza Localidade**
----
 Recebe requisição contendo a hash do contrato e propriedades para atualizar uma localidade.

* **URL**

  {{api-url}}/updateGroup

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| group_token | Obrigatório | Token da localidade |
	| name | Opcional | Identificação da localidade com no mínimo 3 e máximo 30 caracteres |
	| terminals | Opcional | ``["d24f88e6-6466-49f3-9156-58a295cb5f33"]`` |
	| language | Opcional |  |

* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Localidade criado com sucesso!"}` |
	| 400 | `{"error":"Informe uma hash correta."}` |
	| 400 | `{"error":"Nenhuma localidade encontrata."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 400 | `{"error":"Informe o label com 3 a 30 caracteres."}` |
	| 409 | `{"error":"Existe outra localidade com o mesmo nome. Escolha um nome diferente."}` |
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/updateGroup' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","group_token":"{{group_token}}","name":"{{name}}","terminals":"{{terminals}}","language":"{{language}}"}'
  ````

<br/>

**Deleta Localidade**
----
  Recebe requisição contendo a hash do contrato e o token da localidade para exclusão.

* **URL**

  {{api-url}}/deleteGroup

* **Método HTTP:**

  `POST`
  
*  **Parâmetros na URL**

   Nada 

* **Parâmetros**

	| Parâmetro | Recurso | Observação |
	|--|--|--|
	| contract_hash | Obrigatório | Hash do contrato |
	| user_token | Obrigatório | Token do usuário |
	| group_token | Obrigatório | Token da localidade |
	
* **Respostas:**
	
	|Código| Resposta |
	|--|--|
	| 200 | `{"message":"Ajustes aplicados com sucesso!"}` |
	| 400 | `{"error":"Verifique o JSON enviado."}` |
	| 400 | `{"error":"Verifique os parâmetros enviados."}` |
	| 403 | `{"error":"Sem permissão ao recurso."}` |
	| 402 | `{"error":"Nenhum contrato encontrado."}`|
	| 402 | `{"error":"Nenhum token encontrado."}`|
	| 500 | `{"error":"Algo deu errado. Tente novamente."}` |

* **Exemplo:**
	
	````curl
	curl --request POST \
  --url 'http://{{api-url}}/deleteGroup' \
  --header 'Authorization: Basic bW9kYm94LTIuMDowRTk2QTRCNQ==' \
  --header 'Content-Type: application/json' \
  --data '{{"contract_hash":"{{contract_hash}}", "user_token":"{{user_token}}","group_token":"{{group_token}}"'
  ````



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwOTQ4MzIyNF19
-->
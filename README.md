cheat_sheets matérias puc minas

REDIS – COMANDOS BÁSICOS

GET (VARIAVEL QUE FOI CRIADA PARA ARMAZENAR O DADO)   => BUSCA O DADO

KEYS *  => RETORNA TODAS AS VARIAVEIS CRIADAS

set A "candidato1 => CRIA A VARIAVEL E ARMAZENA O DADO

DEL A

LISTA EXTENSA DE COMANDOS NO SITE




Quando usar:
situações de  informações de seção Web são únicas

carrinho de compras e um para cada userid.

Sistema de mensagens para assinantes. No redis você consegue colocar o tempo de vida => set a 5 --→ chave apagada em 5 seg

Não usar:
quando precisa mapear relacionamentos
não há como inspecionar os valores das chaves pelos bancos




Banco de dados de documentos(mongodb)

abordagem agregada que deseja trabalhar com dados na forma de unidades que tenham uma estrutura mais complexa que tuplas.

Agregado é conjunto de objetos relacionados, que facilita o trabalho em cluster

relacionais não possuem conceieto de agregados no modelo de dados
necessidade de conhecer previamente como e o que deseja-se saber sobre os dados

mongo db é bd baseado em documentos. Trabalha com Javascript.








db.albuns.find().pretty()

db.albuns.update({"nome" : "Master of Puppets"}, {$set : {"artista_id" : "1"}});
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })

> db.artistas.insert([ {"nome": "Metallica", "id" : "1"},
... {"nome": "Megadeath", "id" : "2"},
... {"nome": "Slayer", "id" : "3"},
... {"nome": "Anthrax", "id" : "4"},
... {"nome": "Iron Maiden", "id" : "5"},
... {"nome": "Nirvana", "id" : "6"},
... {"nome": "Pink Floyd", "id" : "7"}])

db.albuns.find({"duracao" : {"$in": [1200, 3000]}}).pretty()

> db.albuns.find({"nome":"Seventh Son of a Seventh Son"}).pretty()

db.albuns.insert({"nome": "Seventh Son of a Seventh Son", "artista": "Iron Maiden", "produtor": "Martin Birch", "estudioGravacao": "Musid Studios", "dataLancamento": new Date(1988, 3, 11)})

> db.albuns.find({"nome":" /of/"}).pretty()

var artista = db.artistas.findOne({"nome" : "Metallica"})
> artista




 Instancia do banco – mesma coisa no bd doc
 Esquema – BD
 Tabela – Coleção
 Linha – Documento
 Coluna – Campo
 Id linha – id(id do Documento)
usa { “variavel”: [oqueforarmazenado];
	}
 

mongo db é otimo para registro de eventos.
Gerenciamento de conteudo de web, toda a parte de comunicação na web é por JSON. Por isso é muito usado como servidores da web.
Comercio eletronico por ser mais facil a visualização


Ruim para transações complexas. Operações são atomicas a niveis de documento. Banco por exemplo não utiliza. Em multiplos documentos não é ideal.

Cypher do neo4j
Case sensitive

Deletar 
Match (m:Musico)
Where m.nome = 'Jimmy Hebdrix'
Delete m


Match(Hendrix:Musico{nome:"Jimmy Hendrix"}),(al_along:Musica {nome:"All Along the Watchtower"})
Create (Hendrix)-[r:Gravou]->(al_along)


Deleta todos as ligações
Match (n)-[r]-()
Delete n,r;

CREATE(al_along:Musica {nome: "All Along the Watchtower"})

create(hendrix:Musico {nome : 'Jimmy Hendrix'})
create(dylan:Musico {nome : 'Bob Dylan', data_de_nascimento : '1941-05-24'})

Buscando relacionamentos
match (n1)-[]-()
return n1

Buscando relacionamentos de entrada
match (n1)-[]->()
return n1



Buscando relacionamentos de saída
match ()-[]->(n1)
return n1

Buscando relacionamentos de saída
match ()-[]->(n1)
return count n1

Buscando para visualizar em texto
match (n1)-[r]-(n2:musica)
return n1, type(r), n2
Olhar em texto a relação
Buscando para visualizar em texto
match (n1)-[r:gravou]-(n2:musica)
return n1, type(r), n2
só os com relacionamento gravou


EDITAR NÓ
match (hendrix:Musico {nome: ‘Jimmy Hendrix’})
Set hendrix.data_de_nascimento = “1942-11-27”
Return hendrix

Pode se jogar o null no lugar da data pra excluir o campo

selecionando relacionamento para deletar
Match (hendrix:Musico{nome: ‘Jimmy Hendrix’})-[r]-()
Delete hendrix

deletando o banco todo
Match (n)
Optional Match (n)-[rel]-()
Delete rel, n

Importando arquivos
tem que jogar na pasta que achei fuçando no neo4j cm botao direito
Load CSV WITH Headers
from "file:///composicoes.csv"
As linha
return linha

Load CSV WITH Headers

from "file:///composicoes.csv"
As linha
MERGE (compositor:Musico {nome:linha.compositor})
Merge (musica:Musica {nome: linha.musica})
Merge (compositor)-[:COMPOS]->(musica)

Load CSV WITH Headers
from "file:///gravacoes.csv"
As linha
MERGE (interprete:Musico {nome:linha.interprete})
Merge (musica:Musica {nome: linha.musica})
Merge (interprete)-[:Gravou]->(musica)

match (i:Musico)-[g:Gravou]->(m:Musica)
return i,m


BD relacional para neo4j
Load csv with headers from "file:///products.csv" as row
Create (n:product)
SET n = row,
n.unitPrice = toFloat(row.unitPrice),
n.unitsInStock = toInteger (row.unitsInStock),
n.unitsOnOrder = toInteger (row.unitsOnOrder),
n.reorderLevel = toInteger (row.reorderLevel),
n.discontinued = (row.discontinued <> "0")

Create Index on:product(productID)

Match (p:product),(s:Supplier)
Where p.supplierID = c.supplierID
create (s)-[:supplies]->(p)

1) MATCH (s:Supplier)-->(:Product)-->(c:Category) 2) MATCH (c:Category {categoryName:"Produce"})←-(:Product)←-(s:Supplier)


usar em redes sociais, relacionementos de funcionarios, clientes
não usar qnd apresenta muitas alterações nos nós
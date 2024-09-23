# MongoDB-Momento

# Contém a base de indicados da empresa Momento para treinar consultas complexas no MongoDB.
# Vamos fazer algumas perguntas para brincar de análise exploratória de dados com MongoDB. <br>


1. Quantos funcionarios da empresa Momento trabalham no departamento de vendas? <br>

> db.funcionarios.aggregate([
{
$lookup: { 
from: "departamentos",
localField: "departamento",
foreignField: "_id",
as: "departamento"}}, 
{
$match: {"departamento.nome": "Vendas"}},
{
$count: "total"}])

< total: 1

2. Inclua suas próprias informações no departamento de Tecnologia da empresa. <br>

> db.funcionarios.insertOne({"nome": "Lucas Miranda", "telefone": "232.567.7777", "email": "luquinhas@gmail.org", "dataAdmissao": "2005-02-19", "cargo": "Web Developer", "salario": 5000, "departamento": ObjectId("85992103f9b3e0b3b3c1fe74")})
>
> 
< {
  acknowledged: true,
  insertedId: ObjectId('66f1890e776deda9f178eec8')
}

> db.funcionarios.find({nome: "Lucas Miranda"})
{
  _id: ObjectId('66f1890e776deda9f178eec8'),
  nome: 'Lucas Miranda',
  telefone: '232.567.7777',
  email: 'luquinhas@gmail.org',
  dataAdmissao: '2005-02-19',
  cargo: 'Web Developer',
  salario: 5000,
  departamento: ObjectId('85992103f9b3e0b3b3c1fe74')
}



3. Agora diga, quantos funcionários temos ao total na empresa?


E quanto ao Departamento de Tecnologia?
> db.funcionarios.aggregate([
> {
> $lookup: {
> from: "departamentos",
> localField: "departamento",
> foreignField: "_id",
>  as: "departamento"}},
> {
> $match: {"departamento.nome": "Tecnologia"}},
> {
> $count: "total"}])

< 5

Qual a média salarial do departamento de tecnologia?

Quanto o departamento de Vendas gasta em salários?

Um novo departamento foi criado. O departamento de Inovações. Ele será locado no Brasil. Por favor, adicione-o no banco de dados da empresa colocando quaisquer informações que você achar relevantes.

O departamento de Inovações está sem funcionários. Inclua alguns colegas de turma nesse departamento.

Quantos funcionarios a empresa Momento tem agora?

Quantos funcionários da empresa Momento possuem conjuges?

Qual a média salarial dos funcionários da empresa Momento, excluindo-se o CEO?

Qual a média salarial do departamento de tecnologia?

Qual o departamento com a maior média salarial?

Qual o departamento com o menor número de funcionários?

Pensando na relação quantidade e valor unitario, qual o produto mais valioso da empresa?

Qual o produto mais vendido da empresa?

Qual o produto menos vendido da empresa?

# MongoDB-Momento
**Contém a base de indicados da empresa Momento para treinar consultas complexas no MongoDB.**
**Vamos fazer algumas perguntas para brincar de análise exploratória de dados com MongoDB** <br>


**1. Quantos funcionarios da empresa Momento trabalham no departamento de vendas?** <br>


> db.funcionarios.countDocuments({departamento: ObjectId("85992103f9b3e0b3b3c1fe71")})

< 10


**2. Inclua suas próprias informações no departamento de Tecnologia da empresa.** <br>


> db.funcionarios.insertOne({"nome": "Lucas Miranda", "telefone": "534.777.7577", "email": "luquinhas@gmail.org", "dataAdmissao": "2000-12-20", "cargo": "Web Developer", "salario": 5000, "departamento": ObjectId("85992103f9b3e0b3b3c1fe74")})

< {
  acknowledged: true,
  insertedId: ObjectId('66f18ef359a7898acde11741')
}



**3. Agora diga, quantos funcionários temos ao total na empresa?** <br>
   
> db.funcionarios.countDocuments()

< 24


**4. E quanto ao Departamento de Tecnologia?** <br>

> db.funcionarios.countDocuments({departamento: ObjectId("85992103f9b3e0b3b3c1fe74")})

< 6


**5. Qual a média salarial do departamento de tecnologia?** <br>
> db.funcionarios.aggregate([
  {$match:{departamento: ObjectId("85992103f9b3e0b3b3c1fe74")}},
  {$group: {
    "_id": null,
    "media": {$avg: "salario"}
    }
  }
])

< {
  _id: null,
  media: 4560
}


**6. Quanto o departamento de Vendas gasta em salários?** <br>

> db.funcionarios.aggregate([
  {$match:{departamento: ObjectId("85992103f9b3e0b3b3c1fe71")}},
  {$group: {
    "_id": null,
    "media": {$sum: "salario"}
    }
  }
])

< {
  _id: null,
  soma: 95100
}


**7. Um novo departamento foi criado. O departamento de Inovações. Ele será locado no Brasil. Por favor, adicione-o no banco de dados da empresa colocando quaisquer informações que você achar relevantes.** <br>


**8. O departamento de Inovações está sem funcionários. Inclua alguns colegas de turma nesse departamento.**

**9. Quantos funcionarios a empresa Momento tem agora?**

**10. Quantos funcionários da empresa Momento possuem conjuges?**

**11. Qual a média salarial dos funcionários da empresa Momento, excluindo-se o CEO?**

**12. Qual a média salarial do departamento de tecnologia?**

**13. Qual o departamento com a maior média salarial?**

**14. Qual o departamento com o menor número de funcionários?**

**15.Pensando na relação quantidade e valor unitario, qual o produto mais valioso da empresa?**

**16.Qual o produto mais vendido da empresa?**

**17.Qual o produto menos vendido da empresa?**

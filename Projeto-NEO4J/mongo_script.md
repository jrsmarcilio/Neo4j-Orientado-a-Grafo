# Projeto Orientado a Documentos
<i>Elaborado por Marcílio Júnior</i>

### Objetivo
Realizar a migração de dados do projeto da Unidade 1.

#### Realizar um CRUD geral

 - Cadastrar documentos (insertOne( ) e insertMany( ))

 - Insere um médico
  ```javascript
  db.orientado_documento.insertOne({
    registro: "015974/PE",
    nome: "Dr João Marcio Garcia",
    celular: "(81) 9 9959-7113",
    email: "joão_marcio@mail.com",
    especializacoes: ["Podologista"],
    cep: "55819-068",
    numero: "55"
  });
  ```

 - Insere vários médicos
  ```javascript
  db.orientado_documento.insertMany([
    {
      registro: "067439/PE",
      nome: "Dr Haniel Brião Bulhosa",
      celular: "(81) 9 9999-9999",
      email: "haniel_brião@mail.com",
      especializacoes: ["Gastroenterologista"],
      cep: "54230-661",
      numero: "57"
    },
    {
      registro: "098755/PE",
      nome: "Dr Eliel Filipe Carmona",
      celular: "(81) 9 9999-9999",
      email: "eliel_filipe@mail.com",
      especializacoes: ["Ginecologista"],
      cep: "55819-068",
      numero: "55"
    },
    {
      registro: "099935/PE",
      nome: "Henzo Aquino Matias",
      celular: "(81) 9 9999-9999",
      email: "aquino_matias@mail.com",
      especializacoes: ["Endocrinologista"],
      cep: "55608-312",
      numero: "08"
    },
    {
      registro: "036596/SP",
      nome: "Dra Fabiana Argolo Graça",
      celular: "(81) 9 9999-9999",
      email: "fabiana_argolo@mail.com",
      especializacoes: ["Dermatologista", "Esteticista"],
      cep: "53439-430",
      numero: "55"
    },
    {
      registro: "025189/PE",
      nome: "Dr Jair Doutel Cavadas",
      celular: "(81) 9 9999-9999",
      email: "jair_doutel@mail.com",
      especializacoes: [],
      cep: "54735-330",
      numero: "08"
    },
    {
      registro: "054059/PE",
      nome: "Dra Viviana Telinhos",
      celular: "(81) 9 9999-9999",
      email: "viviana_telinhos@mail.com",
      especializacoes: [],
      cep: "53439-430",
      numero: "5"
    },
  ]);
  ```

 - Insere vários pacientes
  ```javascript
    db.orientado_documento.insertMany([
      {
        "cpf": "311.954.500-79",
        "nome": "Jorge Casqueira Godinho",
        "celular": "(81) 9 9959-7113",
        "email": "jorge_ca@email.com",
        "tiposanguineo": "AB",
        "endereco": {
          "cep": "50610-300",
          "numero": "35"
        }
      },
      {
        "cpf": "353.122.974-53",
        "nome": "Isadora Guterres Bogado",
        "celular": "(81) 8 2760-2296",
        "email": "isadora_gu@email.com",
        "tiposanguineo": "A+",
        "endereco": {
          "cep": "50110-435",
          "numero": "45"
        }
      },
      {
        "cpf": "452.215.184-57",
        "nome": "Melany Moura Saraiva",
        "celular": "(81) 9 2211-2901",
        "email": "melany_mo@email.com",
        "tiposanguineo": "B+",
        "endereco": {
          "cep": "50640-030",
          "numero": "1621"
        }
      },
      {
        "cpf": "934.783.604-47",
        "nome": "Zayn Fernandes Magalhães",
        "celular": "(81) 8 3321-6582",
        "email": "zayn_fe@email.com",
        "tiposanguineo": "O+",
        "endereco": {
          "cep": "50610-300",
          "numero": "888"
        }
      },
      {
        "cpf": "563.576.984-58",
        "nome": "Romeu Meira Modesto",
        "celular": "(81) 9 4539-5543",
        "email": "romeu_ma@email.com",
        "tiposanguineo": "AB+",
        "endereco": {
          "cep": "50110-110",
          "numero": "2165"
        }
      },
      {
        "cpf": "475.444.784-08",
        "nome": "Thomas Porciúncula Regodeiro",
        "celular": "(81) 9 8699-9509",
        "email": "thomas_porciúncula@email.com",
        "tiposanguineo": "A-",
        "endereco": {
          "cep": "51335-220",
          "numero": "1421"
        }
      },
      {
        "cpf": "775.323.504-44",
        "nome": "Zhen Caniça Machado",
        "celular": "(81) 8 4518-8601",
        "email": "zhen_caniça@email.com",
        "tiposanguineo": "B-",
        "endereco": {
          "cep": "52125-150",
          "numero": "714"
        }
      },
      {
        "cpf": "447.896.964-72",
        "nome": "Cloe Valverde Gaspar",
        "celular": "(81) 9 2078-6747",
        "email": "cloe_valverde@email.com",
        "tiposanguineo": "O-",
        "endereco": {
          "cep": "52125-150",
          "numero": "17"
        }
      }
    ]);
  ```

#### Atualizar valores em documentos específicos (updateOne( ), updateMany( ) e replaceOne( ))

 - Atualiza um médico adicionando outra especialização ao seu Array de Especializações
  ```javascript
    db.orientado_documento.updateOne({ registro: "098755/PE" }, { $push: { especializacoes: "Obstretra" } })
  ``` 
 - Atualiza vários médico adicionando um campo salário e atribuindo o valor de 8500
  ```javascript
    db.orientado_documento.updateMany({}, { $set: { salario: 8500 } })
  ``` 
 - Atualiza um médico com filtro pelo registro e atualiza todos os campos
  ```javascript
    db.orientado_documento.replaceOne({ registro: "015974/PE" },{
      registro: "015974/PE",
      nome: "Dr João Marcio Garcia",
      celular: "(81) 9 9959-7113",
      email: "joão_marcio@mail.com",
      especializacoes: ["Podologista"],
      cep: "55819-068",
      numero: "55",
      salario: 9200
    });
  ``` 

#### Deletar documentos baseados em alguma condição(deleteOne( ) e deleteMany( ))

 - Deleta um médico
  ```javascript
    db.orientado_documento.deleteOne({ registro: "015974/PE" })
  ```
- Deleta vários médicos que tem salário maior ou igual a 9200
  ```javascript
    db.orientado_documento.deleteMany({ salario: { $gte: 9200 } })
  ```

#### Selecionar dados (Find( )) 

  ```javascript
    db.orientado_documento.deleteOne({ registro: "015974/PE" })
  ```

  ```javascript
    db.orientado_documento.deleteMany({ salario: { $gte: 9200 } })
  ```

  #### Extra 

  - Percorre os documentos e insere um objeto com o endereco composto por cep e número
  ```javascript
    db.orientado_documento.find().forEach((doc) => {
      db.orientado_documento.updateOne(
        { _id: doc._id }, {
          "$set": { "endereco": { "cep": doc.cep, "numero": doc.numero } },
          "$unset": {"cep": 1, "numero": 1}
        })
    })
  ```
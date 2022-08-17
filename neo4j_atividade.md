OBJETIVO
// Grafo com informações do período 2022 - 1

```javascript
CREATE(Francisco: Professor { nome: 'Francisco do Nascimento', titulacao: 'Doutorado', formacao: 'Ciencia da Computacao', email: 'francisco.junior@jaboatao.ifpe.edu.br' })
CREATE(Diego: Professor { nome: 'Diego dos Passos', titulacao: 'Mestre', formacao: 'Engenharia da Computacao', email: 'diego.silva@jaboatao.ifpe.edu.br' })
CREATE(Josino: Professor { nome: 'Josino Rodrigues', titulacao: 'Mestre', formacao: 'Analise e Desenvolvimento de sistemas', email: 'josino.neto@jaboatao.ifpe.edu.br' })
CREATE(Luciano: Professor { nome: 'Luciano de Souza', titulacao: 'Doutorado', formacao: 'Ciencia da Computacao', email: 'luciano.cabral@jaboatao.ifpe.edu.br' })
CREATE(Ana: Professor { nome: 'Ana Josil Sa Barreto', titulacao: 'Mestrado', formacao: 'Letras', email: 'ana.montenegro@jaboatao.ifpe.edu.br' })

CREATE(Sistemas: Disciplina { nome: 'Sistemas Distribuidos', CH: 60 })
CREATE(WEBII: Disciplina { nome: 'WEB III', CH: 40 })
CREATE(WEBIII: Disciplina { nome: 'WEB II', CH: 80 })
CREATE(Projeto: Disciplina { nome: 'Projeto e Pratica I', CH: 80 })
CREATE(Redes: Disciplina { nome: 'Redes de Computadores', CH: 80 })
CREATE(Seguranca: Disciplina { nome: 'Segurança de Sistemas', CH: 80 })
CREATE(Portugues: Disciplina { nome: 'Portugues Instrumental', CH: 60 })
CREATE(Ingles: Disciplina { nome: 'Ingles I', CH: 60 })
CREATE(Inteligencia: Disciplina { nome: 'Inteligencia Artificial', CH: 60 })

CREATE(ads: Curso { nome: 'ADS', coord: 'Diego dos Passos' })
CREATE(ipi: Curso { nome: 'IPI', coord: 'Francisco do Nascimento' })
CREATE(qualidade: Curso { nome: 'Qualidade', coord: 'Francisco Chaves' })

CREATE(Marcilio: Aluno { nome: 'Marcilio Goncalves Santos Junior', idade: 29, cidade: 'Jaboatao dos Guararapes', formacao: 'N/A' }),
(Talitha: Aluno { nome: 'Talitha Bianka Santana Da Silva Santiago', idade: 18, cidade: 'Recife', formacao: 'N/A' }),
(Mayara: Aluno { nome: 'Mayara Alves De Andrade', idade: 21, cidade: 'Jaboatao dos Guararapes', formacao: 'N/A' }),
(Allan: Aluno { nome: 'Allan Patrick Freire Nascimento', idade: 23, cidade: 'Recife', formacao: 'N/A' }),
(Romullo: Aluno { nome: 'Romullo Gomes De Souza', idade: 24, cidade: 'Jaboatao dos Guararapes', formacao: 'N/A' }),
(Bia: Aluno { nome: 'Ana Beatriz Rodrigues Dos Santos ', idade: 29, cidade: 'Jaboatao dos Guararapes', formacao: 'N/A' })

CREATE (Sistemas)-[:fazparte{ periodo: 1 }]->(ads)
CREATE (WEBII)-[:fazparte{ periodo: 1 }]->(ads)
CREATE (WEBIII)-[:fazparte{ periodo: 1 }]->(ads)
CREATE (Projeto)-[:fazparte{ periodo: 1 }]->(ads)
CREATE (Redes)-[:fazparte{ periodo: 1 }]->(ads)
CREATE (Seguranca)-[:fazparte{ periodo: 1 }]->(ads)
CREATE (Portugues)-[:fazparte{ periodo: 2 }]->(ipi)
CREATE (Ingles)-[:fazparte{ periodo: 2 }]->(ipi)
CREATE (Inteligencia)-[:fazparte{ periodo: 1 }]->(ads)

CREATE (Diego)-[:ministra{ turno: 'manha' }]->(Redes)
CREATE (Diego)-[:ministra{ turno: 'manha' }]->(Seguranca)
CREATE (Josino)-[:ministra{ turno: 'manha' }]->(Sistemas)
CREATE (Josino)-[:ministra{ turno: 'manha' }]->(WEBII)
CREATE (Josino)-[:ministra{ turno: 'manha' }]->(WEBIII)
CREATE (Francisco)-[:ministra{ turno: 'noite' }]->(Projeto)
CREATE (Ana)-[:ministra{ turno: 'noite' }]->(Portugues)
CREATE (Ana)-[:ministra{ turno: 'noite' }]->(Ingles)
CREATE (Luciano)-[:ministra{ turno: 'noite' }]->(Inteligencia)

CREATE (Marcilio)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Ingles)
CREATE (Marcilio)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Redes)
CREATE (Marcilio)-[:pagadisciplina{ MF: 0, semestre: 2, situacao: 'pendente' }]->(Projeto)
CREATE (Marcilio)-[:pagadisciplina{ MF: 0, semestre: 1, situacao: 'pendente' }]->(Sistemas)
CREATE (Marcilio)-[:pagadisciplina{ MF: 7.1, semestre: 1, situacao: 'aprovado' }]->(Seguranca)
CREATE (Marcilio)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(WEBIII)
CREATE (Talitha)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Ingles)
CREATE (Talitha)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Redes)
CREATE (Talitha)-[:pagadisciplina{ MF: 0, semestre: 2, situacao: 'pendente' }]->(Projeto)
CREATE (Talitha)-[:pagadisciplina{ MF: 0, semestre: 1, situacao: 'pendente' }]->(Sistemas)
CREATE (Talitha)-[:pagadisciplina{ MF: 7.1, semestre: 1, situacao: 'pendente' }]->(Inteligencia)
CREATE (Bia)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Portugues)
CREATE (Bia)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Ingles)
```

### Atualizações

#### Atualização do nome Lógica de Programacao para o mesmo nome sem acentos:
```javascript
  MATCH (d:Disciplina { CH: 100 }) SET d.nome = "Logica de Programacao" RETURN *
```

#### Atualização dos relacionamentos dos alunos que não tinham relacionamentos com disciplina
```javascript
  MATCH
      (a1:Aluno { nome: 'Mayara Alves De Andrade' }),
      (a2:Aluno { nome: 'Allan Patrick Freire Nascimento' }),
      (a3:Aluno { nome: 'Romullo Gomes De Souza' }),
      (d1:Disciplina { nome: 'Portugues Instrumental' })
  WITH a1, a2, a3, d1
  CREATE
      (a1)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(d1),
      (a2)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(d1),
      (a3)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(d1)
```

### CONSULTAS

#### SELEÇÃO DE NOME E IDADE DOS ALUNOS QUE CURSARAM LÓGICA DE PROGRAMAÇÃO NO PRIMEIRO PERÍODO DO CURSO ADS
```MATCH(d:Disciplina)-[fp:fazparte{ periodo: 1 }]->(c:Curso{ nome: 'ADS' }) RETURN *```

CREATE(f: Professor {
  nome: 'Francisco do Nascimento',
  titulacao: 'Doutorado',
  formacao: 'Ciencia da Computacao',
  email: 'francisco.junior@jaboatao.ifpe.edu.br'
});
CREATE(d: Professor {
  nome: 'Diego dos Passos',
  titulacao: 'Mestre',
  formacao: 'Engenharia da Computacao',
  email: 'diego.silva@jaboatao.ifpe.edu.br'
});
CREATE(j: Professor {
  nome: 'Josino Rodrigues',
  titulacao: 'Mestre',
  formacao: 'Analise e Desenvolvimento de Sistemas',
  email: 'josino.neto@jaboatao.ifpe.edu.br'
});
CREATE(l: Professor {
  nome: 'Luciano de Souza',
  titulacao: 'Doutorado',
  formacao: 'Ciencia da Computacao',
  email: 'luciano.cabral@jaboatao.ifpe.edu.br'
});
CREATE(a: Professor {
  nome: 'Ana Josil Sa Barreto',
  titulacao: 'Mestrado',
  formacao: 'Letras',
  email: 'ana.montenegro@jaboatao.ifpe.edu.br'
});

CREATE(j1: Disciplina { nome: 'Sistemas Distribuidos', CH: 60 })
CREATE(j2: Disciplina { nome: 'WEB III', CH: 40 })
CREATE(j3: Disciplina { nome: 'WEB II', CH: 80 })

CREATE(f1: Disciplina { nome: 'Projeto e Pratica I', CH: 80 })

CREATE(d1: Disciplina { nome: 'Redes de Computadores', CH: 80 })
CREATE(d2: Disciplina { nome: 'Segurança de Sistemas', CH: 80 })

CREATE(a1: Disciplina { nome: 'Portugues Instrumental', CH: 60 })
CREATE(a2: Disciplina { nome: 'Ingles I', CH: 60 })

CREATE(l1: Disciplina { nome: 'Inteligencia Artificial', CH: 60 })

CREATE(ads: Curso { nome: 'ADS', coord: 'Diego dos Passos' })
CREATE(ipi: Curso { nome: 'IPI', coord: 'Francisco do Nascimento' })
CREATE(qualidade: Curso { nome: 'Qualidade', coord: 'Francisco Chaves' })

CREATE(mg: Aluno {
  nome: 'Marcilio Goncalves Santos Junior',
  idade: 29,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});
CREATE(tb: Aluno {
  nome: 'Talitha Bianka Santana Da Silva Santiago',
  idade: 18,
  cidade: 'Recife',
  formacao: 'N/A'
});
CREATE(ma: Aluno {
  nome: 'Mayara Alves De Andrade',
  idade: 21,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});
CREATE(ap: Aluno {
  nome: 'Allan Patrick Freire Nascimento',
  idade: 23,
  cidade: 'Recife',
  formacao: 'N/A'
});
CREATE(rg: Aluno {
  nome: 'Romullo Gomes De Souza',
  idade: 24,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});
CREATE(ab: Aluno {
  nome: 'Ana Beatriz Rodrigues Dos Santos ',
  idade: 29,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});

CREATE (d)-[:ministra{ turno: 'manha' }]->(d1)
CREATE (d)-[:ministra{ turno: 'manha' }]->(d2)
CREATE (j)-[:ministra{ turno: 'manha' }]->(j1)
CREATE (j)-[:ministra{ turno: 'manha' }]->(j2)
CREATE (j)-[:ministra{ turno: 'manha' }]->(j3)
CREATE (p1)-[:ministra{ turno: 'noite' }]->(d1)
CREATE (a)-[:ministra{ turno: 'noite' }]->(a1)
CREATE (a)-[:ministra{ turno: 'noite' }]->(a2)
CREATE (l)-[:ministra{ turno: 'noite' }]->(l1)

CREATE (mg)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(a2)
CREATE (mg)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(d1)
CREATE (mg)-[:pagadisciplina{ MF: 0, semestre: 2, situacao: 'pendente' }]->(f1)
CREATE (mg)-[:pagadisciplina{ MF: 0, semestre: 1, situacao: 'pendente' }]->(j1)
CREATE (mg)-[:pagadisciplina{ MF: 7.1, semestre: 1, situacao: 'aprovado' }]->(d2)
CREATE (mg)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(j2)
CREATE (tb)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(a2)
CREATE (tb)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(d1)
CREATE (tb)-[:pagadisciplina{ MF: 0, semestre: 2, situacao: 'pendente' }]->(f1)
CREATE (tb)-[:pagadisciplina{ MF: 0, semestre: 1, situacao: 'pendente' }]->(j1)
CREATE (tb)-[:pagadisciplina{ MF: 7.1, semestre: 1, situacao: 'pendente' }]->(l1)
CREATE (ab)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(a1)
CREATE (ab)-[:pagadisciplina{ MF: 9.2, semestre: 2, situacao: 'aprovado' }]->(a2)
CREATE (ab)-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(a2)

CONSULTAS

<!-- Encontre o aluno, cujo o final do sobrenome é Junior"... -->
MATCH (aluno:Aluno) WHERE aluno.nome AS Aluno ends with 'Junior'  RETURN aluno.nome

<!-- Procurar pelo aluno, cuja idade é 21 anos e mora em Recife  -->
MATCH (aluno:Aluno{ cidade: 'Recife' }) WHERE aluno.idade >= 21 RETURN aluno.nome, aluno.idade

<!-- Listagem das disciplinas de cada professor do turno da noite  -->
MATCH (aluno:Aluno{ cidade: 'Recife' }) WHERE aluno.idade >= 21 RETURN aluno.nome, aluno.idade

<!-- Excluir todos os nós e seus relacionamentos -->
MATCH (n) DETACH DELETE n;

<!-- Quantidade de relacionamentos -->
MATCH ()-->() RETURN count(*);

<!-- Quantidade de nós -->
MATCH (n) RETURN count(n);

<!-- Lista de todas as labels -->
CALL db.labels()

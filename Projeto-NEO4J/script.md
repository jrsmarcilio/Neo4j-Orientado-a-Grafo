CREATE(Francisco: Professor {
  nome: 'Francisco do Nascimento',
  titulacao: 'Doutorado',
  formacao: 'Ciencia da Computacao',
  email: 'francisco.junior@jaboatao.ifpe.edu.br'
});
CREATE(Diego: Professor {
  nome: 'Diego dos Passos',
  titulacao: 'Mestre',
  formacao: 'Engenharia da Computacao',
  email: 'diego.silva@jaboatao.ifpe.edu.br'
});
CREATE(Josino: Professor {
  nome: 'Josino Rodrigues',
  titulacao: 'Mestre',
  formacao: 'Analise e Desenvolvimento de s)',
  email: 'josino.neto@jaboatao.ifpe.edu.br'
});
CREATE(Luciano: Professor {
  nome: 'Luciano de Souza',
  titulacao: 'Doutorado',
  formacao: 'Ciencia da Computacao',
  email: 'luciano.cabral@jaboatao.ifpe.edu.br'
});
CREATE(Ana: Professor {
  nome: 'Ana Josil Sa Barreto',
  titulacao: 'Mestrado',
  formacao: 'Letras',
  email: 'ana.montenegro@jaboatao.ifpe.edu.br'
});

CREATE(Sistemas: Disciplina { nome: 'Sistemas Distribuidos', CH: 60 });
CREATE(WEBII: Disciplina { nome: 'WEB III', CH: 40 });
CREATE(WEBIII: Disciplina { nome: 'WEB II', CH: 80 });

CREATE(Projeto: Disciplina { nome: 'Projeto e Pratica I', CH: 80 });

CREATE(Redes: Disciplina { nome: 'Redes de Computadores', CH: 80 });
CREATE(Seguranca: Disciplina { nome: 'Segurança de Sistemas', CH: 80 });

CREATE(Portugues: Disciplina { nome: 'Portugues Instrumental', CH: 60 });
CREATE(Ingles: Disciplina { nome: 'Ingles I', CH: 60 });

CREATE(Inteligencia: Disciplina { nome: 'Inteligencia Artificial', CH: 60 });

CREATE(ads: Curso { nome: 'ADS', coord: 'Diego dos Passos' });
CREATE(ipi: Curso { nome: 'IPI', coord: 'Francisco do Nascimento' });
CREATE(qualidade: Curso { nome: 'Qualidade', coord: 'Francisco Chaves' });

CREATE(Marcilio: Aluno {
  nome: 'Marcilio Goncalves Santos Junior',
  idade: 29,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});
CREATE(Talitha: Aluno {
  nome: 'Talitha Bianka Santana Da Silva Santiago',
  idade: 18,
  cidade: 'Recife',
  formacao: 'N/A'
});
CREATE(Mayara: Aluno {
  nome: 'Mayara Alves De Andrade',
  idade: 21,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});
CREATE(Allan: Aluno {
  nome: 'Allan Patrick Freire Nascimento',
  idade: 23,
  cidade: 'Recife',
  formacao: 'N/A'
});
CREATE(Romullo: Aluno {
  nome: 'Romullo Gomes De Souza',
  idade: 24,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});
CREATE(Ana: Aluno {
  nome: 'Ana Beatriz Rodrigues Dos Santos ',
  idade: 29,
  cidade: 'Jaboatao dos Guararapes',
  formacao: 'N/A'
});

CREATE Diego-[:ministra{ turno: 'manha' }]->(Redes)
CREATE Diego-[:ministra{ turno: 'manha' }]->(Seguranca)
CREATE Josino-[:ministra{ turno: 'manha' }]->(Sistemas)
CREATE Josino-[:ministra{ turno: 'manha' }]->(WEBII)
CREATE Josino-[:ministra{ turno: 'manha' }]->(WEBIII)
CREATE Francisco-[:ministra{ turno: 'noite' }]->(Projeto)
CREATE Ana-[:ministra{ turno: 'noite' }]->(Portugues)
CREATE Ana-[:ministra{ turno: 'noite' }]->(Ingles)
CREATE Luciano-[:ministra{ turno: 'noite' }]->(Inteligencia)

CREATE Marcilio-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Ingles)
CREATE Marcilio-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Redes)
CREATE Marcilio-[:pagadisciplina{ MF: 0, semestre: 2, situacao: 'pendente' }]->(Projeto)
CREATE Marcilio-[:pagadisciplina{ MF: 0, semestre: 1, situacao: 'pendente' }]->(Sistemas)
CREATE Marcilio-[:pagadisciplina{ MF: 7.1, semestre: 1, situacao: 'aprovado' }]->(Seguranca)
CREATE Marcilio-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(WEBIII)
CREATE Talitha-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Ingles)
CREATE Talitha-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Redes)
CREATE Talitha-[:pagadisciplina{ MF: 0, semestre: 2, situacao: 'pendente' }]->(Projeto)
CREATE Talitha-[:pagadisciplina{ MF: 0, semestre: 1, situacao: 'pendente' }]->(Sistemas)
CREATE Talitha-[:pagadisciplina{ MF: 7.1, semestre: 1, situacao: 'pendente' }]->(Inteligencia)
CREATE Ana-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Portugues)
CREATE Ana-[:pagadisciplina{ MF: 9.2, semestre: 2, situacao: 'aprovado' }]->(Matematica)
CREATE Ana-[:pagadisciplina{ MF: 10, semestre: 2, situacao: 'aprovado' }]->(Ingles)

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

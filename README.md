# OHospitalFundamental
Um hospital local precisa desenvolver um sistema para gerenciar seus dados clínicos e substituir planilhas e arquivos antigos por um banco de dados funcional. O objetivo é criar uma estrutura que registre médicos, pacientes, consultas, convênios, receitas médicas e muito mais...  

PARTE 2

No hospital, as internações têm sido registradas por meio de formulários eletrônicos que gravam os dados em arquivos. 
Para cada internação, são anotadas a data de entrada, a data prevista de alta e a data efetiva de alta, além da descrição textual dos procedimentos a serem realizados. 
As internações precisam ser vinculadas a quartos, com a numeração e o tipo. 
Cada tipo de quarto tem sua descrição e o seu valor diário (a princípio, o hospital trabalha com apartamentos, quartos duplos e enfermaria).
Também é necessário controlar quais profissionais de enfermaria estarão responsáveis por acompanhar o paciente durante sua internação. Para cada enfermeiro(a), é necessário nome, CPF e registro no conselho de enfermagem (COREN).
A internação, obviamente, é vinculada a um paciente – que pode se internar mais de uma vez no hospital – e a um único médico responsável.

R:
```js
db["internações"].insertMany([
  {
    dataEntrada: new Date("2024-10-02"),
    dataPrevistaAlta: new Date("2024-11-10"),
    dataEfetivaAlta: new Date("2024-10-25"),
    procedimentos: ["Colecistectomia, administração de antibióticos"],
    quarto: 
    {
      numero: 101,
      tipo: 
      {
        descricao: "Apartamento",
        valorDiario: 300.00
      }
    },
    enfermeirosResponsaveis: [
      {
        nome: "Maria Silva",
        cpf: "123.178.592-90",
        coren: "SP123456"
      },
      {
        nome: "Carlos Souza",
        cpf: "123.456.789-00",
        coren: "SP654321"
      }
    ],
    paciente: 
    {
      nome: "João Santos",
      cpf: "987.654.321-00",
      dataNascimento: new Date("1995-02-14")
    },
    medicoResponsavel: 
    {
      nome: "Dra. Ana Souza",
      crm: "SP12345"
    }
  },
  {
    dataEntrada: new Date("2024-10-03"),
    dataPrevistaAlta: new Date("2024-12-29"),
    dataEfetivaAlta: new Date("2025-01-05"),
    procedimentos: ["Hemostasia Cirúrgica, administração de anticoagulantes"],
    quarto:
    {
      numero: 102,
      tipo: 
      {
        descricao: "Quarto Duplo",
        valorDiario: 200.00
      }
    },
    enfermeirosResponsaveis: [
      {
        nome: "Paula Lima",
        cpf: "123.456.789-09",
        coren: "SP789012"
      }
    ],
    paciente: 
    {
      nome: "Maria Oliveira",
      cpf: "876.543.210-09",
      dataNascimento: new Date("1987-11-30")
    },
    medicoResponsavel: 
    {
      nome: "Dr. Carlos Pereira",
      crm: "SP54321"
    }
  },
  {
    dataEntrada: new Date("2024-10-05"),
    dataPrevistaAlta: new Date("2024-10-12"),
    dataEfetivaAlta: new Date("2024-10-11"),
    procedimentos: ["Cirurgia ortopédica, fisioterapia pós-operatória"],
    quarto: 
    {
      numero: 103,
      tipo: 
      {
        descricao: "Enfermaria",
        valorDiario: 150.00
      }
    },
    enfermeirosResponsaveis: [
      {
        nome: "José Santos",
        cpf: "037.643.210-00",
        coren: "SP345678"
      }
    ],
    paciente: 
    {
      nome: "Roger Federer",
      cpf: "122.133.414-15",
      dataNascimento: new Date("1981-08-08")
    },
    medicoResponsavel: 
    {
      nome: "Dr. Roberto Dias",
      crm: "SP67890"
    }}]);
```
PARTE 3

Inclua ao menos dez médicos de diferentes especialidades.

R:

# O Hospital Fundamental
Um hospital local precisa desenvolver um sistema para gerenciar seus dados clínicos e substituir planilhas e arquivos antigos por um banco de dados funcional. O objetivo é criar uma estrutura que registre médicos, pacientes, consultas, convênios, receitas médicas e muito mais...  

# PARTE 2

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
# PARTE 3

- Inclua ao menos dez médicos de diferentes especialidades. Ao menos sete especialidades (considere a afirmação de que “entre as especialidades há pediatria, clínica geral, gastrenterologia e dermatologia”).

R:
```js
db["medicos"].insertMany([
  {
    _id: ObjectId(),
    nome: "Dr. John Watson",
    data_nascimento": new Date("1852-07-07"),
    especialidades": "Medicina Geral",
    tipo: "Especialista",
    contato: {"telefone": "24567-2346","email": "elementary@gmail.com"},
    documentos: {"cpf": "23456789012","CRM": "JW001"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Hannibal Lecter",
    data_nascimento: new Date("1938-01-01"),
    especialidades: "Psiquiatria",
    tipo: "Especialista",
    contato: {"telefone": "24567-2348","email": "hannibal.lecter@psych.com"},
    documentos: {"cpf": "45678901234","CRM": "HL001"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Abraham Van Helsing",
    data_nascimento: new Date("1850-01-01"),
    especialidades: "Dermatologia",
    tipo: "Especialista",
    contato: {"telefone": "24567-2359","email": "vanhelsing@gmail.com"},
    documentos: {"cpf": "56789012345","CRM": "VH001"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Sócrates",
    data_nascimento: new Date("1954-02-19"),
    especialidades: "Medicina Esportiva",
    tipo: "Especialista",
    contato: {"telefone": "21910-1977","email": "thedoctor@gmail.com"},
    documentos: {"cpf": "44455566677","CRM": "SB12345"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Manhattan",
    data_nascimento: new Date("1959-01-01"),
    especialidades: "Psicologia",
    tipo: "Especialista",
    contato: {"telefone": "22555-0456","email": "manhattan@hotmail.com"},
    documentos: {"cpf": "33333333333","CRM": "DM002"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Otto Octavius",
    data_nascimento: new Date("1963-01-01"),
    especialidades: "Cirurgia Geral",
    tipo: "Especialista",
    contato": {"telefone": "12555-2020","email": "0tt0ctavius@hotmail.com" },
    documentos": {"cpf": "88888888888","CRM": "DO007"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dra. Harley Quinzel",
    data_nascimento: new Date("1990-01-01"),
    especialidades: "Psiquiatria",
    tipo: "Especialista",
    contato": {"telefone": "24567-2360","email": "harleyquinn@gmail.com"},
    documentos": {"cpf": "12345678900","CRM": "HQ002"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Luke Skywalker",
    data_nascimento: new Date("1930-08-30"),
    especialidades: "Cardiologia",
    tipo: "Especialista",
    contato": {"telefone": "24567-2353", "email": "luke.skywalker@gmail.com"},
    documentos: {"cpf": "90123456789","CRM": "SW004"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Jekyll",
    data_nascimento: new Date("1930-08-30"),
    especialidades: "Cirurgia Geral",
    tipo: "Especialista",
    contato: {"telefone": "24567-2354", "email": "jekyll@hotmail.com"},
    documentos: {"cpf": "01234567890","CRM": "SW005"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Stephen Strange",
    data_nascimento: new Date("1978-06-02"),
    especialidades: "Neurologia",
    tipo: "Residente",
    contato: {"telefone": "24567-2355", "email": "doutorestranho@gmail.com"},
    documentos: {"cpf": "12345678901","CRM": "SH002"},
    status: 1
  },
  {
    _id: ObjectId(),
    nome: "Dr. Gregory House",
    data_nascimento: new Date("1968-03-24"),
    especialidades: "Infectologia",
    tipo: "Especialista",
    contato: {"telefone": "24567-2357", "email": "house@hotmail.com"},
    documentos: {"cpf": "34567890123","CRM": "UY456"},
    status: 1
  }
]);
```

-Inclua ao menos 15 pacientes.

R:
```js
db["pacientes"].insertMany([
  {
    _id: ObjectId(),
    nome: "Diego Palacios",
    data_nascimento: new Date("1999-07-12"),
    altura: "1.69",
    endereco: {logradouro: "Rua Oliveira",numero: "245",bairro: "Itaquera",
    cidade: "São Paulo",estado: "SP",CEP: "02961080"},
    contato: {telefone: "95167-9887",email: "diegopala@gmail.com"},
    convenio: {nome: "Unimed",validate: new Date("2025-02-24"),CNPJ: "123456781010101",carencia: "80"},
    documentos: {CPF: "21678689002",RG: "12.345.678-9"}
  },
  {
    _id: ObjectId(),
    nome: "Diego Maradona",
    data_nascimento: new Date("1960-10-30"),
    altura: "1.65",
    endereco: {logradouro: "Rua Augusta",numero: "10",bairro: "Boca",
    cidade: "Buenos Aires",estado: "BA",CEP: "05002010"},
    contato: {telefone: "91123-4567", email: "lamanodedios@gmail.com"},
    convenio: {nome: "Unimed",validate: new Date("2025-12-31"),CNPJ: "12345678901234", carencia: "100"},
    documentos: {CPF: "12345645900",RG: "12.345.656-9"}
  },
  {
    _id: ObjectId(),
    nome: "Edson Arantes",
    data_nascimento: new Date("1940-10-23"),
    altura: "1.73",
    endereco: {logradouro: "Rua Edson Arantes",numero: "10",bairro: "Santos",
    cidade: "Três Corações", estado: "MG", CEP: "11000010"},
    contato: {telefone: "13567-8901",email: "pele@gmail.com"},
    convenio: {nome: "Bradesco Saúde",validate: new Date("2024-08-15"),CNPJ: "98765432100101", carencia: "90"},
    documentos: {CPF: "98765432100",RG: "98.765.432-1"}
  },
  {
    _id: ObjectId(),
    nome: "Johan Cruyff",
    data_nascimento: new Date("1947-04-25"),
    altura: "1.78",
    endereco: {logradouro: "Rua Amsterdam",numero: "14",bairro: "Ajax",
    cidade: "Amsterdã",estado: "ND",CEP: "10120000"},
    contato: {telefone: "10123-4567",email: "cruyff@gmail.com"},
    convenio: {nome: "Unimed", validate: new Date("2023-11-30"),CNPJ: "23456789012345",carencia: "60"},
    documentos: {CPF: "34567890123",RG: "34.567.890-1"}
  },
  {
    _id: ObjectId(),
    nome: "Zinedine Zidane",
    data_nascimento: new Date("1972-06-23"),
    altura: "1.85",
    endereco: {logradouro: "Rua França",numero: "10",bairro: "Marselha",
    cidade: "Marselha",estado: "PR",CEP: "13002010"},
    contato: {telefone: "91234-5678",email: "zizou@gmail.com"},
    convenio: {nome: "Unimed",validate: new Date("2026-03-20"),CNPJ: "45678901234567",carencia: "70"},
    documentos: {CPF: "45678901234",RG: "45.678.901-2"}
  },
  {
    _id: ObjectId(),
    nome: "Ronaldo De Assis",
    data_nascimento: new Date("1980-03-21"),
    altura: "1.81",
    endereco: {logradouro: "Rua Porto Alegre",numero: "10",bairro: "Cruzeiro",
    cidade: "Porto Alegre",estado: "RS", CEP: "90100010"},
    contato: {telefone: "12345-6789",email: "ronaldinho@gmail.com"},
    convenio: {nome: "Unimed",validate: new Date("2024-12-31"),CNPJ: "87654321098765",carencia: "50"},
    documentos: {CPF: "76543210987",RG: "76.543.210-9"}
  },
  {
    _id: ObjectId(),
    nome: "Paul Pogba",
    data_nascimento: new Date("1993-03-15"),
    altura: "1.91",
    endereco: {logradouro: "Rua Corso Gaetano",numero: "8",bairro: "Vecchia Signora",
    cidade: "Torino",estado: "IT",CEP: "M160RA"},
    contato: {telefone: "91456-7890", email: "ppgba@gmail.com"},
    convenio: {nome: "Saúde",validate: new Date("2024-08-12"), CNPJ: "65478901234567",carencia: "90"},
    documentos: {CPF: "54321098765",RG: "54.321.098-7"}
  },
  {
    _id: ObjectId(),
    nome: "Yuri Alberto",
    data_nascimento: new Date("2001-03-18"),
    altura: "1.83",
    endereco: {logradouro: "Rua do Goleador",numero: "9",bairro: "Itaquera",
    cidade: "São Paulo",estado: "SP",CEP: "02961080"},
    contato: {telefone: "91234-6789",email: "YuriAlberto@gmail.com"},
    convenio: {nome: "Saúde",validate: new Date("2025-05-01"),
    CNPJ: "76543210987654",carencia: "60"},
    documentos: {CPF: "65432109876",RG: "65.432.109-8"}
  },
{
    _id: ObjectId(),
    nome: "Cristiano Ronaldo",
    data_nascimento: new Date("1985-02-05"),
    altura: "1.87",
    endereco: {logradouro: "Rua dos Galáticos",numero: "7",bairro: "Madeira",
    cidade: "Funchal",estado: "PT",CEP: "90000001"},
    contato: {telefone: "91234-5678",email: "cristiano.ronaldo@gmail.com"},
    convenio: {nome: "Unimed",validate: new Date("2028-03-31"),CNPJ: "98765432000150",carencia: "60"},
    documentos: {CPF: "12345678909",RG: "99.999.999-9"}
},
  {
    _id: ObjectId(),
    nome: "André Ramalho",
    data_nascimento: new Date("1992-02-16"),
    altura: "1.82",
    endereco: {logradouro: "Rua Do Zagueiro Mediano",numero: "87",bairro: "Itaquera",
    cidade: "São Paulo",estado: "SP",CEP: "18150000"},
    contato: {telefone: "91234-5678",email: "andreramalho@gmail.com"},
    convenio: {nome: "Unimed",validate: new Date("2025-06-30"),CNPJ: "32109876543210",carencia: "120"},
    documentos: {CPF: "10987654321",RG: "10.987.654-3"}
  },
  {
    _id: ObjectId(),
    nome: "Roberto Rivelino",
    data_nascimento: new Date("1946-01-01"),
    altura: "1.73",
    endereco: {logradouro: "Rua Corinthians",numero: "10",bairro: "Itaquera",
    cidade: "São Paulo",estado: "SP",CEP: "01134000"},
    contato: {telefone: "92765-1234",email: "rivelino@gmail.com"},
    convenio: {nome: "Sáude",validate: new Date("2024-03-20"),CNPJ: "87654321098765",carencia: "90"},
    documentos: {CPF: "21098765432",RG: "21.098.765-4"}
  },
  {
    _id: ObjectId(),
    nome: "Arthur Antunes Coimbra",
    data_nascimento: new Date("1953-03-03"),
    altura: "1.72",
    endereco: {logradouro: "Rua Flamengo",numero: "10",bairro: "Gávea",
    cidade: "Rio de Janeiro",estado: "RJ",CEP: "22451000"},
    contato: {telefone: "93847-1122",email: "galinho@gmail.com"},
    convenio: {nome: "Unimed", validate: new Date("2026-08-10"),CNPJ: "65432109876543",carencia: "70"},
    documentos: {CPF: "32109876543",RG: "32.109.876-5"}
  };
  {
    _id: ObjectId(),
    nome: "Lionel Messi",
    data_nascimento: new Date("1987-06-24"),
    altura: "1.70",
    endereco: {logradouro: "Calle de la Paz", numero: "10", bairro: "Rosário",
    cidade: "Santa Fé", estado: "AR", CEP: "03980000"},
    contato: {telefone: "99988-7766", email: "thegoat@gmail.com"},
    convenio: {nome: "Unimed", validate: new Date("2025-05-30"), CNPJ: "12345678000190", carencia: "60"},
    documentos: {CPF: "12345678900",RG: "12.345.678-9"}
};
{
    _id: ObjectId(),
    nome: "Luis Suárez",
    data_nascimento: new Date("1987-01-24"),
    altura: "1.82",
    endereco: { logradouro: "Avenida de la Mordida", numero: "9",bairro: "Jardim Elba",
    cidade: "Uruguai",estado: "AR",CEP: "50000"},
    contato: {telefone: "98876-5432",email: "pistoleiro@gmail.com"},
    convenio: {nome: "La Caja",validate: new Date("2026-03-20"),CNPJ: "98765432000110",carencia: "90"},
    documentos: {CPF: "23456789012", RG: "98.765.432-0"}
};
{
    _id: ObjectId(),
    nome: "Neymar Jr.",
    data_nascimento: new Date("1992-02-05"),
    altura: "1.75",
    endereco: {logradouro: "Rua Domingos",numero: "11",bairro: "Santos",
    cidade: "São Paulo",estado: "SP",CEP: "11040000"
    },
    contato: {telefone: "97765-4321",email: "neymar@gmail.com"},
    convenio: {nome: "Bradesco Saúde",validate: new Date("2024-12-31"),CNPJ: "65432178000120",carencia: "30"},
    documentos: {CPF: "98765432101", RG: "34.567.890-1"}
}
]);
```

-Registre 20 consultas de diferentes pacientes e diferentes médicos (alguns pacientes realizam mais que uma consulta). As consultas devem ter ocorrido entre 01/01/2015 e 01/01/2022. Ao menos dez consultas devem ter receituário com dois ou mais medicamentos.

R: 
```js
db["consultas"].insertMany([
  {
    _id: ObjectId(),
    paciente: { nome: "Alice Santos", data_nascimento: new Date("1990-05-15"),  
    contato: { telefone: "98765-4321", email: "aliceWonderland@gmail.com" }},
    medico: {nome: "Dr. John Marston",especialidade: "Medicina Geral"},
    data: new Date("2015-03-12"),
    receituario: {medicamentos: [{ nome: "Paracetamol", dosagem: "500mg" },{ nome: "Ibuprofeno", dosagem: "200mg" }],
    observacoes: "Tomar após as refeições."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Raul Gustavo", data_nascimento: new Date("1985-09-25"),
    contato: {telefone: "91234-5678", email: "raulzinho@gmail.com" }},
    medico: {nome: "Dr. Hannibal Lecter",especialidade: "Psiquiatria"},
    data: new Date("2016-06-01"),
    receituario: {medicamentos: [{ nome: "Lithium", dosagem: "20mg" }],
    observacoes: "Reavaliação em 30 dias."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Carlos Miguel",data_nascimento: new Date("1975-02-14"),
    contato: {telefone: "99876-5432", email: "carlosmiguellz@gmail.com"}},
    medico: {nome: "Dr. John Watson",especialidade: "Medicina Geral"},
    data: new Date("2017-04-20"),
    receituario: {medicamentos: [{ nome: "Amoxicilina", dosagem: "500mg" },{ nome: "Cetirizina", dosagem: "10mg" }],
    observacoes: "Fazer uso por 7 dias."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Sarah Palmer ",data_nascimento: new Date("1950-11-10"),
    contato: { telefone: "96543-2109", email: "palmer@gmail.com" }},
    medico: {nome: "Dr. Sócrates",especialidade: "Medicina Esportiva"},
    data: new Date("2018-01-15"),
    receituario: {medicamentos: [{ nome: "Glicose", dosagem: "5g" },],
    observacoes: "Hidratar-se bem após a atividade."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Eduardo Lima",data_nascimento: new Date("1980-07-30"),
    contato: { telefone: "98765-0123", email: "eduardo@gmail.com" }},
    medico: {nome: "Dr. Manhattan",especialidade: "Psicologia"},
    data: new Date("2019-09-01"),
    receituario: {medicamentos: [{ nome: "Sertralina", dosagem: "50mg" }],
    observacoes: "Reavaliação daqui a 15 dias."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Fernanda Costa", data_nascimento: new Date("1988-03-22"),
    contato: { telefone: "92345-6789", email: "nandinha@gmail.com" }},
    medico: {nome: "Dr. Otto Octavius",especialidade: "Cirurgia Geral"},
    data: new Date("2015-12-12"),
    receituario: {medicamentos: [{ nome: "Paracetamol", dosagem: "500mg" }, { nome: "Dipirona", dosagem: "1g" }],
    observacoes: "Tomar a cada 8 horas."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Anthony Soprano",data_nascimento: new Date("1966-04-08"),
    contato: { telefone: "97456-7890", email: "tonysoprano@gmail.com" }},
    medico: {nome: "Dra. Harley Quinzel",especialidade: "Psiquiatria"},
    data: new Date("2020-02-20"),
    receituario: {medicamentos: [{ nome: "Prozac", dosagem: "0.5mg" },{ nome: "Lithium", dosagem: "75mg" }],
    observacoes: "Tomar ao acordar."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Hugo Souza",data_nascimento: new Date("1983-05-14"),
    contato: { telefone: "95123-4567", email: "hugo@gmail.com" }},
    medico: {nome: "Dr. Gregory House",especialidade: "Infectologia"},
    data: new Date("2019-08-12"),
    receituario: {medicamentos: [{ nome: "Azitromicina", dosagem: "500mg" },{ nome: "Paracetamol", dosagem: "500mg" }],
    observacoes: "Fazer uso dos medicamentos por 7 dias."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Isabela Rocha", data_nascimento: new Date("1993-12-01"),
    contato: { telefone: "96123-9876", email: "belarochaa@gmail.com" }},
    medico: {nome: "Dr. Roger", especialidade: "Medicina Geral"},
    data: new Date("2019-06-15"),
    receituario: {medicamentos: [{ nome: "Nimesulida", dosagem: "100mg" },{ nome: "Dorflex", dosagem: "10mg" }],
    observacoes: "Tomar antes das refeições."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "William Carvalho",data_nascimento: new Date("1991-08-22"),
    contato: { telefone: "97531-8642", email: "william@gmail.com" }},
    medico: {nome: "Dr. Raimundo",especialidade: "Endocrinologia"},
    data: new Date("2020-11-11"),
    receituario: {medicamentos: [{ nome: "Insulina", dosagem: "15 unidades" }],
    observacoes: "Verificar a glicemia diariamente."}
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Anna De Souza",data_nascimento: new Date("1987-07-18"),
    contato: { telefone: "99876-5432", email: "aNNaSouza@gmail.com" }},
    medico: {nome: "Dr. Robertson",especialidade: "Medicina Geral"},
    data: new Date("2021-05-05"),
    receituario: {medicamentos: [{ nome: "Dipirona", dosagem: "1g" }],
    observacoes: "Tomar a cada 6 horas"
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Bruno Melo",data_nascimento: new Date("1994-01-29"),
    contato: { telefone: "96321-4567", email: "Bruno@gmail.com" }},
    medico: {nome: "Dr. Abraham Van Helsing",especialidade: "Dermatologia"},
    data: new Date("2021-09-21"),
    receituario: {medicamentos: [{ nome: "Diclofenaco", dosagem: "100mg" },{ nome: "Paracetamol", dosagem: "500mg" }],
    observacoes: "Aplicar compressa quente após 30 minutos."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Paul Pogba",data_nascimento: new Date("1993-03-15"),
    contato: { telefone: "91919-1919", email: "ppgba@gmail.com" }},
    medico: {nome: "Dr. Sócrates",especialidade: "Medicina Esportiva"},
    data: new Date("2021-06-22"),
    receituario: {medicamentos: [{ nome: "Lorazepam", dosagem: "100mg" },{ nome: "Ibuprofeno", dosagem: "200mg" }],
    observacoes: "Tomar após a atividade física."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Renato Augusto",data_nascimento: new Date("1987-10-30"),
    contato: { telefone: "96512-3456", email: "renat8augusto@gmail.com" }},
    medico: {nome: "Dr. João Silva",especialidade: "Medicina Geral"},
    data: new Date("2015-05-25"),
    receituario: {medicamentos: [{ nome: "Lorazepam", dosagem: "100mg" }],
    observacoes: "Evitar a condução de veículos."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Caio Ribeiro",data_nascimento: new Date("1979-04-12"),
    contato: { telefone: "93456-7890", email: "caioba@gmail.com" }},
    medico: {nome: "Dr. John Watson",especialidade: "Medicina Geral"},
    data: new Date("2016-12-20"),
    receituario: {medicamentos: [{ nome: "Ciprofloxacino", dosagem: "500mg" },{ nome: "Omeprazol", dosagem: "20mg" }],
    observacoes: "Tomar sempre antes do almoço."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Diego Palacios", data_nascimento: new Date("1999-07-12"),
    contato: { telefone: "91234-5678", email: "diegopala@gmail.com" }},
    medico: {nome: "Dr. Stephen Strange", especialidade: "Neurologia"},
    data: new Date("2019-11-09"),
    receituario: {medicamentos: [{ nome: "Gabapentina", dosagem: "300mg" },{ nome: "Duloxetina", dosagem: "60mg" }],
    observacoes: "Reavaliação em 30 dias."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Yuri Alberto", data_nascimento: new Date("1998-01-02"),
    contato: { telefone: "93210-5432", email: "YuriAlberto@gmailcom"}},
    medico: { nome: "Dr. Luke Skywalker",especialidade: "Cardiologia"},
    data: new Date("2021-03-22"),
    receituario: { medicamentos: [{ nome: "Atorvastatina", dosagem: "10mg" },{ nome: "Losartana", dosagem: "50mg" }],
    observacoes: "Verificar a pressão arterial diariamente."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Weverton", data_nascimento: new Date("1987-03-15"),
    contato: { telefone: "94832-1234", email: "wevvrt@gmail.com" }},
    medico: {nome: "Dr. Alex Poatan", especialidade: "Infectologia"},
    data: new Date("2019-10-15"),
    receituario: {medicamentos: [{ nome: "Ibuprofeno", "dosagem": "400mg" },{ nome: "Azitromicina", "dosagem": "500mg" }],
    observacoes: "Tomar antibiótico por 7 dias."
    }
},
{
    _id: ObjectId(),
    paciente: {nome: "Franklin",data_nascimento: new Date("1946-01-01"),
    contato: { "telefone": "94231-4321", "email": "franklin@gmail.com" }},
    medico: {nome: "Dr. Abraham Van Helsing",especialidade: "Medicina Geral"},
    data: new Date("2020-07-18"),
    receituario: {medicamentos: [{ "nome": "Omeprazol", "dosagem": "20mg" },{ nome: "Paracetamol", "dosagem": "500mg" }],
    observacoes: "Evitar alimentos gordurosos."
    }
},
{
    _id: ObjectId(),
    paciente: {nome: "Cristiano Ronaldo",data_nascimento: new Date("1985-02-05"),
    contato: { "telefone": "93145-6789", "email": "cr7@gmail.com" }},
    medico: {nome: "Dr. Hannibal Lecter", especialidade: "Psiquiatria"},
    data: new Date("2021-11-10"),
    receituario: {medicamentos: [{ nome: "Clonazepam", "dosagem": "2mg" },{ nome: "Diazepam", "dosagem": "5mg" }],
    observacoes: "Uso controlado. Retornar em 30 dias."
    }
}
]);
```

- Inclua ao menos quatro convênios médicos, associe ao menos cinco pacientes e cinco consultas.

R:
```js
[
  {
    _id: ObjectId(),
    paciente: {nome: "Yuri Alberto", data_nascimento: new Date("1998-01-02"),
    contato: { telefone: "93210-5432", email: "yuri@gmail.com" },
    convenio: { nome: "Porto Seguro", validate: new Date("2025-02-24"), CNPJ: "123456781010101", carencia: "80" }},
    medico: {nome: "Dr. Alfred Pennyworth", especialidade: "Cardiologia"},
    data: new Date("2021-03-22"),
    receituario: {medicamentos: [{ nome: "Atorvastatina", "dosagem": "10mg" },{ nome: "Losartana", "dosagem": "50mg" }],
    observacoes: "Verificar a pressão arterial diariamente."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Paul Pogba", data_nascimento: new Date("1993-03-15"),
    contato: { telefone: "94832-1234", email: "pogba@gmail.com" },
    convenio: { nome: "Amil", validate: new Date("2023-08-12"), CNPJ: "987654321234567", carencia: "90" }},
    medico: {nome: "Dr. Gregory House", especialidade: "Infectologia"},
    data: new Date("2019-10-15"),
    receituario: {medicamentos: [{ nome: "Ibuprofeno", "dosagem": "400mg" },{ nome: "Azitromicina", "dosagem": "500mg" }],
    observacoes: "Tomar antibiótico por 7 dias."
    }
  },
  {
    _id: ObjectId(),
    paciente: {nome: "Rivelino", data_nascimento: new Date("1946-01-01"),
    contato: { telefone: "94231-4321", email: "rivelino@gmail.com" },
    convenio: { nome: "SulAmérica", validate: new Date("2024-05-14"),  CNPJ: "112233445566778", carencia: "60" }},
    medico: {nome: "Dr. Abraham Van Helsing",especialidade: "Medicina Geral"},
    data: new Date("2020-07-18"),
    receituario: {medicamentos: [{ nome: "Omeprazol", "dosagem": "20mg" },{ nome: "Paracetamol", "dosagem": "500mg" }],
    observacoes: "Evitar alimentos gordurosos."
    }
  },
  {
   _id: ObjectId(),
   paciente: {nome: "Cristiano Ronaldo",data_nascimento: new Date("1985-02-05"),
   contato: { "telefone": "93145-6789", "email": "cr7@gmail.com" },
   convenio: { "nome": "Bradesco Saúde", "validate": new Date("2023-12-31"), "CNPJ": "223344556677889", "carencia": "45" }},
   medico: {nome: "Dr. Hannibal Lecter",especialidade: "Psiquiatria"},
   data: new Date("2021-11-10"),
   receituario: {medicamentos: [{ nome: "Clonazepam", "dosagem": "2mg" },{nome: "Diazepam", "dosagem": "5mg" }],
   observacoes: "Uso controlado. Retornar em 30 dias."
    }
  },
  {
  _id: ObjectId(),
  paciente: {nome: "Breno Bidon",data_nascimento: new Date("1997-09-21"),
  contato: { telefone: "94222-7878", email: "breno@gmail.com" },
  convenio: { nome: "Unimed", validate: new Date("2026-04-20"), CNPJ: "998877665544332", carencia: "30" }},
  medico: {nome: "Dr. Otto Octavius", especialidade: "Cirurgia Geral"},
  data: new Date("2020-05-16"),
  receituario: {medicamentos: [{nome: "Dipirona", "dosagem": "1g" },{ nome: "Cetoprofeno", "dosagem": "100mg" }],
  observacoes: "Tomar após as refeições."}
  }
]
```

- Criar entidade de relacionamento entre médico e especialidade.

R:

![image](https://github.com/user-attachments/assets/95e26387-e859-42c8-b10c-437caef1ad5d)


- Criar Entidade de Relacionamento entre internação e enfermeiro.

R:

![image](https://github.com/user-attachments/assets/d33713d9-f7b1-4c37-9288-b52afeec2d1a)


- Arrumar a chave estrangeira do relacionamento entre convênio e médico.



- Registre ao menos sete internações. Pelo menos dois pacientes devem ter se internado mais de uma vez. Ao menos três quartos devem ser cadastrados. As internações devem ter ocorrido entre 01/01/2015 e 01/01/2022.

```js
db.internacoes.insertMany([
  {
    paciente: "João Santos",
    dataEntrada: ISODate("2016-03-10T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2016-03-17T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2016-03-16T00:00:00.000Z"),
    quarto: { _id: "1a", numero: 101 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dra. Ana Souza",
    procedimentos: ["Cirurgia de apendicite"]
  },
  {
    paciente: "João Santos",
    dataEntrada: ISODate("2018-01-15T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2018-01-22T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2018-01-23T00:00:00.000Z"),
    quarto: { _id: "1b", numero: 202 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dr. João Silva",
    procedimentos: ["Exame de sangue", "Raio-X"]
  },
  {
    paciente: "Maria Oliveira",
    dataEntrada: ISODate("2017-06-01T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2017-06-08T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2017-06-08T00:00:00.000Z"),
    quarto: { _id: "1a", numero: 101 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dr. Roberto Dias",
    procedimentos: ["Cirurgia ortopédica"]
  },
  {
    paciente: "Maria Oliveira",
    dataEntrada: ISODate("2020-09-20T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2020-09-27T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2020-09-28T00:00:00.000Z"),
    quarto: { _id: "1b", numero: 202 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dr. Roberto Dias",
    procedimentos: ["Exame de sangue", "Raio-X"]
  },
  {
    paciente: "Diego Palacios",
    dataEntrada: ISODate("2019-12-02T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2019-12-09T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2019-12-08T00:00:00.000Z"),
    quarto: { _id: "1c", numero: 303 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dr. João Silva",
    procedimentos: ["Cirurgia de hérnia"]
  },
  {
    paciente: "Diego Maradona",
    dataEntrada: ISODate("2021-05-15T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2021-05-22T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2021-05-21T00:00:00.000Z"),
    quarto: { _id: "1a", numero: 101 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dra. Ana Souza",
    procedimentos: ["Tratamento de infecção"]
  },
  {
    paciente: "Diego Maradona",
    dataEntrada: ISODate("2017-07-10T00:00:00.000Z"),
    dataPrevistaAlta: ISODate("2017-07-17T00:00:00.000Z"),
    dataEfetivaAlta: ISODate("2017-07-18T00:00:00.000Z"),
    quarto: { _id: "1B", numero: 202 },
    enfermeirosResponsaveis: "Enfermeira Maria Silva",
    medicoResponsavel: "Dr. Roberto Dias",
    procedimentos: ["Tratamento respiratório"]
  }
])
```

- Considerando que “a princípio o hospital trabalha com apartamentos, quartos duplos e enfermaria”, inclua ao menos esses três tipos com valores diferentes.

R: 
```js
db.quartos.insertMany([
  {
    numero: "102",
    tipo: "Quarto Duplo",
    valor: 200
  },
  {
    numero: "101",
    tipo: "Apartamento",
    valor: 300
  },
  {
    numero: "103",
    tipo: "Enfermaria",
    valor: 150
  }
]);
```

- Inclua dados de dez profissionais de enfermaria. Associe cada internação a ao menos dois enfermeiros.

R: 

```js
db.enfermeiros.insertMany([

  {
    _id: ObjectId(),
    nome: "Enfermeiro Daniele De Rossi",
    CPF: "98765432100",
    registro_CRE: "CRE67890",
    data_nascimento: ISODate("1983-07-15T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeiro Andrea Barzagli",
    CPF: "03764321000",
    registro_CRE: "CRE03764",
    data_nascimento: ISODate("1981-05-25T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeiro Mehdi Benatia",
    CPF: "12345678900",
    registro_CRE: "CRE12345",
    data_nascimento: ISODate("1992-06-08T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeira Victoria Albuquerque",
    CPF: "16672678909",
    registro_CRE: "CRE16672",
    data_nascimento: ISODate("1990-03-20T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeira Antonio Rudiger",
    CPF: "22345678901",
    registro_CRE: "CRE22345",
    data_nascimento: ISODate("1993-02-03T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeira Gabriela Zanotti",
    CPF: "11223344556",
    registro_CRE: "CRE11223",
    data_nascimento: ISODate("1991-09-11T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeiro John Terry",
    CPF: "55667788990",
    registro_CRE: "CRE55667",
    data_nascimento: ISODate("1980-12-07T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeira Andressa Alves",
    CPF: "99887766554",
    registro_CRE: "CRE99887",
    data_nascimento: ISODate("1995-01-14T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeiro Thomas Müller",
    CPF: "44556677889",
    registro_CRE: "CRE44556",
    data_nascimento: ISODate("1988-03-30T00:00:00.000Z")
  },
  {
    _id: ObjectId(),
    nome: "Enfermeira Rayssa Leal",
    CPF: "33445566778",
    registro_CRE: "CRE33445",
    data_nascimento: ISODate("1994-08-18T00:00:00.000Z")
  }
]);
```
```js
db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a5259") }, 
  {$set:
      {enfermeirosResponsaveis: [ObjectId("66e98acfa294ca7f32df1370"), ObjectId("66e98acfa294ca7f32df1375")]}
  }
);

db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a525a") }, 
  {$set:
     {enfermeirosResponsaveis: [ObjectId("66e98acfa294ca7f32df1376"), ObjectId("66e98acfa294ca7f32df1371") ]}
  }
);

db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a525b") }, 
  {$set:
     {enfermeirosResponsaveis: [ ObjectId("66e98acfa294ca7f32df1373"),ObjectId("66e98acfa294ca7f32df136e") ]}
  }
);

db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a525c") }, 
  {$set:
    {enfermeirosResponsaveis: [ObjectId("66e98acfa294ca7f32df136f"), ObjectId("66e98acfa294ca7f32df1372")]}
  }
);

db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a525d") }, 
  {$set:
    {enfermeirosResponsaveis: [ObjectId("66e98acfa294ca7f32df1379"), ObjectId("66e98acfa294ca7f32df1378")]}
  }
);

db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a525e") }, 
  {$set:
    {enfermeirosResponsaveis: [ObjectId("66e98acfa294ca7f32df1374"), ObjectId("66e98acfa294ca7f32df1373")]}
  }
);

db.internacoes.updateMany(
  { _id: ObjectId("671714589b88976e823a525f") }, 
  {$set:
    {enfermeirosResponsaveis: [ObjectId("66e98acfa294ca7f32df1375"), ObjectId("66e98acfa294ca7f32df136e")]}
  }
);
```
# PARTE 4
- Crie um script que adicione uma coluna “em_atividade” para os médicos, indicando se ele ainda está atuando no hospital ou não. Crie um script para atualizar ao menos dois médicos como inativos e os demais em atividade.

R:
```js
db.medicos.updateMany({},
  {$set:{em_atividade: true}}
);

db.medicos.updateOne(
  { _id: ObjectId("670d58299fee93319230d9f8") }, 
  {$set: {em_atividade: false}}
);

db.medicos.updateOne(
  { _id: ObjectId("670d58299fee93319230d9f9") }, 
  {$set: {em_atividade: false}}
);
```

# PARTE 5
Criar um script de consultas nesse banco de dados

1- Todos os dados e o valor médio das consultas do ano de 2020 e das que foram feitas sob convênio

R:
```js
db.consultas.aggregate([
  {$match:
    {
      data:
      {$gte: ISODate("2020-01-01T00:00:00.000Z"),
       $lt: ISODate("2021-01-01T00:00:00.000Z")}
    }
  },
  {$group:
     {  
      _id: null,
      totalConsultas: { $sum: 1 },
      mediaValor: { $avg: "$valor" },
      dadosConsultas: { $push: "$$ROOT" }
     }
  } //esse é o script para saber o valor das consultas de 2020
]);
```
```js
db.consultas.aggregate([
  {$match:
    {conveniado: true}
  },
  {$group:
    {
      _id: null,
      totalConsultas: { $sum: 1 },
      mediaValor: { $avg: "$valor" },
      dadosConsultas: { $push: "$$ROOT"}
    } //esse é o script para saber as consultas feitas através de um convênio
  }]);
```
2- Todos os dados das internações que tiveram data de alta maior que a data prevista para a alta

R:
```js
db.internacoes.aggregate([
  {$match:
    {dataEfetivaAlta: { $exists: true }, dataPrevistaAlta: { $exists: true }}
  },
  {$match:
    {$expr:
      {$gt: ["$dataEfetivaAlta", "$dataPrevistaAlta"]}
    }
  }
]);
```
3- Receituário completo da primeira consulta registrada com receituário associado

R:
```js
db.consultas.aggregate([
  { $sort: { data: 1 }},
  { $limit: 1 },
  {$lookup:
     {
      from: "receituario",
      localField: "receituario._id",
      foreignField: "_id",
      as: "receituarioDetalhes"
     }
  },
  {$project:
     {
      _id: 1, paciente: 1, data: 1,
      receituarioDetalhes: {$arrayElemAt: ["$receituarioDetalhes", 0]}
     }
  }
]);
```
4-Todos os dados da consulta de maior valor e também da de menor valor (ambas as consultas não foram realizadas sob convênio)

R:
```js
db.consultas.aggregate([
  { $match: { convenio: { $exists: false } } },
  { $group: { _id: null, maiorValor: { $max: "$valor" }, menorValor: { $min: "$valor" } } },
  { $lookup: { from: "consultas", localField: "maiorValor", foreignField: "valor", as: "consultaMaior" } },
  { $lookup: { from: "consultas", localField: "menorValor", foreignField: "valor", as: "consultaMenor" } },
  { $project:
   {
     consultaMenor: { $arrayElemAt: ["$consultaMaior", 0] },
     consultaMMaior: { $arrayElemAt: ["$consultaMenor", 0] }
   } 
  }
]);
```
5- Todos os dados das internações em seus respectivos quartos, calculando o total da internação a partir do valor de diária do quarto e o número de dias entre a entrada e a alta.

R:
```js
db.internacoes.aggregate([
  {$addFields:
      {
      diasInternacao:
      {
        $subtract: [
          { $toDate: "$data_efetiva_alta" },
          { $toDate: "$data_entrada" }
        ]
      },
      totalInternacao:
      {
        $multiply: [
          { $dateDiff: { startDate: "$data_entrada", endDate: "$data_efetiva_alta", unit: "day" } },
          "$valor_diario"
        ]
    }}},
  {$project:
    {
      _id: 1, paciente_id: 1, medico_id: 1,
      data_entrada: 1, data_prevista_alta: 1, data_efetiva_alta: 1,
      procedimentos: 1, quarto_numero: 1, valor_diario: 1,
      enfermeiro_id: 1, diasInternacao: 1, totalInternacao: 1
    }
  }
]);
```
6- Data, procedimento e número de quarto de internações em quartos do tipo “apartamento”.

R:
```js
db.internacoes.aggregate([
    {$match: {"quarto_numero": 101}
    },
    {$project:
        {
            "_id": 0,
            "data_entrada": 1, "procedimentos": 1, "quarto_numero": 1
        }
    }
  ])
```
7- Nome do paciente, data da consulta e especialidade de todas as consultas em que os pacientes eram menores de 18 anos na data da consulta e cuja especialidade não seja “pediatria”, ordenando por data de realização da consulta.

R:
```js

```
8- Nome do paciente, nome do médico, data da internação e procedimentos das internações realizadas por médicos da especialidade “gastroenterologia”, que tenham acontecido em “enfermaria”.

R:
```js
```

9- Os nomes dos médicos, seus CRMs e a quantidade de consultas que cada um realizou.

R:
```js
```

10-Todos os médicos que tenham "Gabriel" no nome. 

R:
```js
```

11-Os nomes, CORENs e número de internações de enfermeiros que participaram de mais de uma internação.

R:
```js
```

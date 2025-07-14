# 🏥 Sistema de Gerenciamento Hospitalar – BANCOO

Este repositório contém a modelagem de um **banco de dados relacional** para um sistema hospitalar. O banco visa centralizar informações sobre pacientes, médicos, consultas, especialidades, receitas e funcionários.

---

## 🗂️ Entidades e Estrutura

### 👤 PACIENTES

| Campo             | Tipo         | Descrição                     | Restrições      |
|------------------|--------------|-------------------------------|-----------------|
| id_paciente       | INT          | Identificador único           | PRIMARY KEY     |
| nome              | VARCHAR(255) | Nome do paciente              | NOT NULL        |
| data_nascimento   | DATE         | Data de nascimento            | NOT NULL        |
| endereco          | VARCHAR(255) | Endereço                      | NOT NULL        |
| telefone          | VARCHAR(15)  | Telefone                      | NOT NULL        |
| email             | VARCHAR(255) | E-mail                        | NOT NULL        |
| sexo              | VARCHAR(10)  | Sexo                          | NOT NULL        |
| tipo_sanguineo    | VARCHAR(3)   | Tipo sanguíneo                | NOT NULL        |

---

### 🥼 MÉDICOS

| Campo         | Tipo         | Descrição                     | Restrições      |
|---------------|--------------|-------------------------------|-----------------|
| id_medico     | INT          | Identificador único           | PRIMARY KEY     |
| nome          | VARCHAR(255) | Nome do médico                | NOT NULL        |
| crm           | VARCHAR(20)  | Registro CRM                  | UNIQUE, NOT NULL|
| telefone      | VARCHAR(15)  | Telefone                      | NOT NULL        |
| email         | VARCHAR(255) | E-mail                        | NOT NULL        |
| especialidade | INT          | ID da especialidade           | FOREIGN KEY     |

---

### 🩺 ESPECIALIDADES

| Campo           | Tipo         | Descrição                     | Restrições      |
|-----------------|--------------|-------------------------------|-----------------|
| id_especialidade| INT          | ID da especialidade           | PRIMARY KEY     |
| nome            | VARCHAR(100) | Nome da especialidade         | NOT NULL        |

---

### 📅 CONSULTAS

| Campo           | Tipo         | Descrição                     | Restrições      |
|-----------------|--------------|-------------------------------|-----------------|
| id_consulta     | INT          | Identificador da consulta     | PRIMARY KEY     |
| id_paciente     | INT          | Paciente relacionado          | FOREIGN KEY     |
| id_medico       | INT          | Médico responsável            | FOREIGN KEY     |
| data_consulta   | DATE         | Data da consulta              | NOT NULL        |
| diagnostico     | VARCHAR(255) | Diagnóstico realizado         | NOT NULL        |
| id_receita      | INT          | Receita vinculada             | FOREIGN KEY     |

---

### 💊 RECEITAS

| Campo         | Tipo     | Descrição                        | Restrições     |
|---------------|----------|----------------------------------|----------------|
| id_receita    | INT      | Identificador da receita         | PRIMARY KEY    |
| id_medico     | INT      | Médico que emitiu                | FOREIGN KEY    |
| id_paciente   | INT      | Paciente que recebeu             | FOREIGN KEY    |
| data_receita  | DATE     | Data da emissão                  | NOT NULL       |
| descricao     | TEXT     | Detalhes da prescrição           | NOT NULL       |

---

### 🧑‍💼 FUNCIONÁRIOS

| Campo        | Tipo           | Descrição                    | Restrições     |
|--------------|----------------|------------------------------|----------------|
| id_funcionario | INT          | Identificador do funcionário | PRIMARY KEY    |
| nome         | VARCHAR(255)   | Nome                         | NOT NULL       |
| cargo        | VARCHAR(100)   | Cargo                        | NOT NULL       |
| sexo         | CHAR(1)        | Sexo                         | NOT NULL       |
| telefone     | VARCHAR(15)    | Telefone                     | NOT NULL       |
| email        | VARCHAR(255)   | E-mail                       | NOT NULL       |
| salario      | DECIMAL(10,2)  | Salário                      | NOT NULL       |

---

## 🔗 Relacionamentos

- Um **médico** está associado a **uma especialidade**.
- Um **paciente** pode ter **múltiplas consultas e receitas**.
- Cada **consulta** está vinculada a um **médico, paciente e receita**.
- As **receitas** são associadas a **consultas e médicos**.

---

## 📌 Observações Técnicas

- Utilização de **chaves primárias e estrangeiras** para garantir integridade referencial.
- Tipagem adequada para dados sensíveis como CPF, datas e valores monetários.
- Campos `NOT NULL` asseguram obrigatoriedade de dados essenciais.

---

## 📄 Licença

Este projeto é de uso educacional. Licenciado sob a [MIT License](LICENSE).

---

## ✍️ Autores

Sistema modelado por **Gabriel e Leandro**.

---

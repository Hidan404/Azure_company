# Azure_company

# Transformação de Dados - Power BI

Esse repositório contém o processo de transformação de dados que fiz utilizando o Power BI. O objetivo é preparar os dados para análises mais precisas e criar relatórios e gráficos úteis para o negócio. Segui um conjunto de diretrizes para garantir que os dados estivessem prontos para visualizações significativas.

## Diretrizes de Transformação de Dados

Abaixo estão as diretrizes que utilizei para transformar os dados e deixá-los prontos para o Power BI. Cada etapa tem como foco a limpeza, organização e integração dos dados de uma maneira eficaz.

### 1. **Verificar Cabeçalhos e Tipos de Dados**
O primeiro passo foi conferir os cabeçalhos das colunas e garantir que os tipos de dados estavam corretos. Isso é super importante para que os dados sejam interpretados corretamente. No Power Query, ajustei os tipos de dados para garantir que cada coluna tivesse o tipo correto (texto, número, data, etc.).

### 2. **Corrigir Valores Monetários para o Tipo Double**
Revisei as colunas com valores monetários e fiz a conversão para o tipo `Double` (ou `Decimal Número`). Isso ajudou a garantir precisão nos cálculos financeiros, evitando possíveis erros em análises posteriores.

### 3. **Verificar Nulos e Analisar a Remoção**
Passei pelas colunas em busca de valores nulos. Quando encontrei, tomei decisões sobre como tratá-los. Em alguns casos, removi as linhas com nulos, e em outros substituí esses valores por algo mais apropriado, para não comprometer as análises.

### 4. **Identificar Funcionários Sem Gerente**
Na tabela de funcionários, fiz uma análise para identificar os colaboradores sem gerente (valores nulos na coluna `Super_ssn`). Esses colaboradores provavelmente são os próprios gerentes, então eu verifiquei os dados para confirmar isso.

### 5. **Verificar Departamentos Sem Gerente**
Revisei a tabela de departamentos para ver se havia algum departamento sem gerente (valores nulos na coluna `Mgr_ssn`). Quando encontrei, tratei esses dados de forma a garantir que todos os departamentos estivessem completos e com informações de gerente.

### 6. **Preencher Lacunas de Departamentos Sem Gerente**
Se algum departamento estava sem gerente, fiz o preenchimento com dados fictícios ou conhecidos, para garantir que o modelo de dados estivesse sempre completo e sem lacunas.

### 7. **Verificar Horas dos Projetos**
Na coluna `Hours`, fiz uma verificação para garantir que os valores de horas dos projetos estavam dentro de uma faixa razoável. Se encontrei valores fora do esperado, apliquei ajustes ou substituições, conforme necessário.

### 8. **Separar Colunas Complexas**
Se encontrei colunas que misturavam mais de uma informação (como nome e sobrenome em uma coluna), separei essas informações em colunas distintas. Isso facilita a organização e análise dos dados.

### 9. **Mesclar Tabelas de `employee` e `department`**
Uma das etapas mais importantes foi mesclar as tabelas `employee` e `department`, para associar os funcionários aos departamentos. Utilizei a coluna `Dno` na tabela `employee` e a coluna `Dnumber` na tabela `department` para realizar a junção. Usei uma junção **Left Outer** para garantir que todos os funcionários fossem mantidos, mesmo aqueles que não tinham departamento associado.

### 10. **Remover Colunas Desnecessárias**
Após a mesclagem e outros ajustes, identifiquei e removi colunas que não agregavam valor à análise. Isso ajudou a deixar o modelo de dados mais limpo e eficiente.

### 11. **Associar Funcionários aos Seus Gerentes**
Aqui, fiz uma junção na tabela `employee` consigo mesma, para associar os funcionários aos seus gerentes. Usei a coluna `Super_ssn` (que contém o SSN do gerente) e a coluna `Ssn` (que contém o SSN do colaborador) para fazer essa associação.

### 12. **Mesclar Nome e Sobrenome dos Funcionários**
Juntei as colunas de nome e sobrenome dos funcionários em uma única coluna chamada **Nome Completo**. Isso facilitou a visualização e a apresentação dos dados.

### 13. **Mesclar Departamento e Localização**
Combinei as colunas de **Dname** (Nome do Departamento) e **Dlocation** (Localização) em uma coluna chamada **Departamento-Localização**. Isso garantiu que cada combinação de departamento e local fosse única, o que facilita a análise e visualização.

### 14. **Mesclar vs. Atribuir**
Ao longo de todo o processo, utilizei **mesclagens** de tabelas em vez de atribuições diretas de valores. Isso porque, quando trabalhamos com dados de diferentes tabelas, a melhor prática é a mesclagem. Já a atribuição de valores seria útil apenas para ajustes dentro de uma mesma tabela.

---

## **Banco de Dados Utilizado**

Embora minha intenção inicial tenha sido utilizar o Azure para o cadastro e gerenciamento do banco de dados, enfrentei algumas dificuldades no processo de cadastro e configuração da plataforma. Por conta disso, optei por usar um banco de dados **local com MySQL**. Com isso, consegui configurar e conectar o Power BI ao banco de dados local sem maiores complicações, garantindo um fluxo de trabalho mais estável para a análise dos dados.

---

## Conclusão

Seguindo essas diretrizes, consegui transformar os dados de forma eficiente, tornando-os mais limpos e prontos para análise. O modelo de dados resultante é robusto e livre de lacunas, o que permite gerar relatórios e gráficos significativos. Agora, os dados estão prontos para serem analisados, oferecendo insights valiosos para o negócio.

---

### Como usar este repositório

1. Clone este repositório para sua máquina local.
2. Importe os dados processados para o Power BI.
3. Abra o Power Query e veja as transformações realizadas.
4. Crie relatórios e gráficos baseados nos dados processados.

---

Esse é o processo que segui para transformar os dados e deixá-los prontos para análise. Se você tiver alguma dúvida ou sugestão, fique à vontade para abrir uma issue ou enviar um pull request!


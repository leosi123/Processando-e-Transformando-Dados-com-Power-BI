# Processando-e-Transformando-Dados-com-Power-BI
Desafio DIO - Processando e Transformando Dados com Power BI
Descrição do desafio módulo 3 – Processamento de Dados Simplificado com Power BI

1. Criação de uma instância na Azure para MySQL
   Foi criado um recurso no Azure para banco de dados Mysql, além disso foram configuradas questão de rede como adição IP e permissão de acesso publico para que seja possivel realizar o treinamento.

Foram utilizados os scripts fornecidos pela intrutora para criação de tabelas e inserção de dados. o Script de criação de tabelas continha alguns erros como o comando de deletar colunas foreign key. O comando correto seria: alter table departament drop FOREIGN KEY departament_ibfk_1;
Além de algumas constraints que estavam erradas. Então as removi e inseri os dados.
Diretrizes para transformação dos dados

1. Verifique os cabeçalhos e tipos de dados
-Verigfique todos os tipos de dados e nomes de colunas e me certifiquei se todos tinham nomes
2. Modifique os valores monetários para o tipo double preciso
Foram verificados todos os valores moentarios, porem nao existia nenhum.
3. Verifique a existência dos nulos e analise a remoção
Não exisitam valores nulos, a nao ser o supervisor de um chefe, porem nesse caso ele nao tem chefe. Dessa maneira tudo certo.
4. Os employees com nulos em Super_ssn podem ser os gerentes. Verifique se há algum colaborador sem gerente
Como disse na pergunta 3 existe o James Borg que nao tem gerente
5. Verifique se há algum departamento sem gerente
Não existe
6. Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas

7. Verifique o número de horas dos projetos
Numero de horas dos projetos estava OK, porem um estava como 0, este deveria ser analisado junto com a áre de negocio.
8. Separar colunas complexas
Coluna de endereço foi separada em numero, cidade e estado.
9. Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores. A mescla terá como base a tabela employee. Fique atento, essa informação influencia no tipo de junção
Foram mescladas as colunas com base na coluna Dno da employee e Dnumber da departament.
10. Neste processo elimine as colunas desnecessárias.
Foram eliminadas
11. Realize a junção dos colaboradores e respectivos nomes dos gerentes . Isso pode ser feito com consulta SQL ou pela mescla de tabelas com Power BI. Caso utilize SQL, especifique no README a query utilizada no processo.
Foi feito com o proprio power BI. Foir feita uma mescla de tabelas entre employee e a emplyee através da coluna super_ssn e ssn trazendo o primeiro e último nome do colaborador que tinha o Super_ssn (gerente)
12. Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores
Adicionando uma coluna foi utilzada a linguagem M para concatenar (Text.combine) o nome e sobrenome do colaborador. Em seguida foram removidas as colunas Fname e Lname, mantivemos somente a nova coluna com o nome completo.
13. Mescle os nomes de departamentos e localização. Isso fará que cada combinação departamento-local seja único. Isso irá auxiliar na criação do modelo estrela em um módulo futuro.
Feito através de mescla de tabelas employee dno e dept_locations (dnumber), assim conseguimos obter o local do departamento.
14. Explique por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir.
No caso usamos mesclar para ter a relação entre departamento e local.
15. Agrupe os dados a fim de saber quantos colaboradores existem por gerente
Em seguida utilizamos a função agrupar por gerente e contar linhas
16. Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela
17. Foram eliminadas as colunas desnecessárias para o processo.

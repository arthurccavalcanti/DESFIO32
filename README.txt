Este documento descreve as atividades realizadas para o gerenciamento e aprimoramento do banco de dados Company para o curso da DIO. As atividades incluem ajustes de tipo de dados, análise de nulos, verificação de dados ausentes, e a criação de novas visualizações e consultas SQL para melhorar a estrutura e análise dos dados.
Atividades Realizadas
1. Verificação de Cabeçalhos e Tipos de Dados

    Objetivo: Garantir que todos os cabeçalhos das tabelas e tipos de dados estejam corretos.
    Ação: Revise os cabeçalhos das tabelas e confirme que os tipos de dados correspondem às necessidades dos dados armazenados.

2. Modificação dos Valores Monetários

    Objetivo: Alterar o tipo de dados para maior precisão nos valores monetários.

    Ação: Modificar a coluna Salary e outras colunas monetárias de DECIMAL para DOUBLE com precisão necessária.

3. Verificação e Análise de Nulos

    Objetivo: Identificar e analisar a presença de valores nulos nas tabelas.

    Ação: Verificar a existência de valores nulos e determinar se devem ser removidos ou substituídos.


4. Identificação de Colaboradores sem Gerente

    Objetivo: Verificar se há empregados sem um gerente atribuído.

    Ação: Identificar colaboradores cujo Super_ssn está nulo e analisar se eles são gerentes.

5. Verificação de Departamentos sem Gerente

    Objetivo: Identificar departamentos sem gerente atribuído.

    Ação: Verificar se há departamentos sem um gerente associado.

  
6. Preenchimento de Departamentos sem Gerente

    Objetivo: Preencher informações para departamentos sem gerente.

    Ação: Atualizar a tabela departament com os dados necessários para preencher as lacunas.


7. Verificação do Número de Horas dos Projetos

    Objetivo: Verificar e analisar as horas alocadas para cada projeto.

    Ação: Consultar a tabela works_on para obter a soma das horas trabalhadas por projeto.


8. Separação de Colunas Complexas

    Objetivo: Dividir colunas complexas em colunas mais simples.

    Ação: Criar novas colunas para armazenar dados que eram combinados em uma única coluna.


9. Mesclagem de Consultas entre employee e departament

    Objetivo: Criar uma tabela que mostra o nome dos departamentos associados aos colaboradores.

    Ação: Realizar uma junção entre employee e departament.


10. Eliminação de Colunas Desnecessárias

    Objetivo: Remover colunas que não serão usadas em relatórios.

    Ação: Eliminar colunas desnecessárias de cada tabela.


11. Junção dos Colaboradores com Nomes dos Gerentes

    Objetivo: Associar os nomes dos colaboradores com seus respectivos gerentes.

    Ação: Usar SQL para realizar a junção, ou utilizar ferramentas como Power BI.


12. Mesclagem dos Nomes e Sobrenomes dos Colaboradores

    Objetivo: Consolidar as colunas Fname e Lname em uma única coluna Full_Name.

    Ação: Mesclar as colunas Fname e Lname.


13. Mesclagem dos Nomes de Departamentos e Localizações

    Objetivo: Criar uma combinação única de nome de departamento e localização.

    Ação: Concatenar Dname e Dlocation.


14. Justificativa para Mesclagem ao Invés de Atribuição

    Explicação: A mesclagem é usada para criar uma coluna que combina dados de duas colunas existentes, facilitando análises futuras e garantindo a unicidade. A atribuição não é adequada neste caso porque não combina os dados em uma única coluna.

15. Agrupamento de Dados por Gerente

    Objetivo: Contar o número de colaboradores por gerente.

    Ação: Agrupar os dados e contar o número de colaboradores para cada gerente.



16. Eliminação de Colunas Desnecessárias para Relatórios

    Objetivo: Remover colunas que não são necessárias para relatórios.

    Ação: Limpar as tabelas eliminando colunas que não serão usadas.

///////////////////

Mesclar x Atribuir

1. Mesclar Colunas

Mesclar colunas refere-se ao processo de combinar o conteúdo de duas ou mais colunas em uma nova coluna única. Isso é frequentemente usado para criar uma coluna que sintetiza informações de várias colunas ou para criar identificadores únicos a partir de múltiplos atributos.
Quando Usar:

    Quando você deseja combinar valores de várias colunas em uma coluna única.
    Quando você precisa criar uma coluna de chave composta ou concatenar informações para análise.

Como Fazer:

    No Power Query Editor:
        Selecionar Colunas: Escolha as colunas que você deseja mesclar.
        Mesclar Colunas: Vá para a guia "Transformar" e selecione "Mesclar Colunas".
        Definir Delimitador: Escolha um delimitador, como um espaço ou hífen, para separar os valores combinados.
        Aplicar: A nova coluna será criada contendo os valores mesclados.

    Exemplo:
    Se você tem colunas FirstName e LastName e deseja criar uma coluna FullName, você pode mesclar essas colunas.

    plaintext

FirstName | LastName | FullName
--------------------------------
John      | Doe      | John Doe
Jane      | Smith    | Jane Smith

No DAX:

    Criar Coluna Calculada: Use a função CONCATENATE ou o operador & para criar uma nova coluna.

DAX

    FullName = [FirstName] & " " & [LastName]

2. Atribuir Colunas

Atribuir colunas geralmente refere-se à operação de adicionar uma nova coluna ao conjunto de dados existente ou alterar o valor de uma coluna com base em alguma lógica ou condição.
Quando Usar:

    Quando você precisa criar uma nova coluna com valores derivados de outras colunas ou cálculos.
    Quando você deseja atualizar valores existentes em uma coluna com base em uma fórmula ou regra.

Como Fazer:

    No Power Query Editor:
        Adicionar Coluna: Use a guia "Adicionar Coluna" para criar uma nova coluna com valores calculados.
        Colunas Personalizadas: Crie uma coluna personalizada usando fórmulas M para derivar valores de outras colunas.

    Exemplo:
    Adicionar uma coluna que calcula o preço com desconto.

    M

= Table.AddColumn(PreviousStep, "DiscountedPrice", each [Price] * 0.9)

No DAX:

    Criar Coluna Calculada: Use DAX para criar uma coluna que aplica fórmulas aos dados existentes.

DAX

    DiscountedPrice = [Price] * 0.9

Comparação:

    Mesclar Colunas:
        Combina valores de várias colunas em uma coluna única.
        Útil para criar identificadores únicos ou colunas de texto combinadas.
        Geralmente realizado no Power Query Editor ou usando DAX para concatenação.

    Atribuir Colunas:
        Adiciona ou modifica colunas com base em cálculos ou regras.
        Útil para adicionar dados derivados ou novos valores calculados.
        Realizado no Power Query Editor para transformações ou em DAX para cálculos baseados em regras.

Conclusão:

    Mesclar é mais sobre combinar dados de várias colunas para criar uma nova coluna com uma visão consolidada dos dados.
    Atribuir é mais sobre adicionar novos dados ou modificar dados existentes com base em cálculos ou regras.

Ambas as operações são essenciais para a transformação e análise de dados no Power BI e são usadas conforme as necessidades específicas de modelagem e análise de dados do projeto.

Query SQL utilizada:

  SELECT e.Fname AS Employee_First_Name, e.Lname AS Employee_Last_Name, m.Fname AS Manager_First_Name, m.Lname AS Manager_Last_Name
  FROM employee e
  LEFT JOIN employee m ON e.Super_ssn = m.Ssn
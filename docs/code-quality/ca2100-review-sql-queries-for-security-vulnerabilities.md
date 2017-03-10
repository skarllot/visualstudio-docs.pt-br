---
title: "CA2100: revisar consultas SQL para vulnerabilidades de seguran&#231;a | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Review SQL queries for security vulnerabilities"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
  - "CA2100"
helpviewer_keywords: 
  - "CA2100"
  - "ReviewSqlQueriesForSecurityVulnerabilities"
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2100: revisar consultas SQL para vulnerabilidades de seguran&#231;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|  
|CheckId|CA2100|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um método define a propriedade de <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> usando uma cadeia de caracteres que é criada a partir de um argumento de cadeia de caracteres para o método.  
  
## Descrição da Regra  
 Esta regra presume que o argumento de cadeia de caracteres contém a entrada do usuário.  Uma cadeia de caracteres de comando SQL que é criada da entrada do usuário é vulnerável a ataques de injeção SQL.  Em um ataque de injeção SQL, um usuário mal\-intencionado fornece entrada que modificar o design de uma consulta na tentativa de danificar ou ter acesso não autorizado a base de dados subjacente.  As técnicas básicas incluem a injeção de uma aspa simples ou de apóstrofo, que é o delimitador de cadeia de caracteres literal SQL; dois características, que significa um comentário SQL; e um ponto\-e\-vírgula, que indica que um novo comando a seguir.  Se a entrada de usuário deve fazer parte da consulta, use uma das opções a seguir, listados em ordem de eficiência, para reduzir o risco de ataque.  
  
-   Use um procedimento armazenado.  
  
-   Use uma cadeia de caracteres de comando com parâmetros.  
  
-   Validar entrada do usuário para o tipo e o conteúdo antes de compilar a cadeia de caracteres de comando.  
  
 Os seguintes tipos de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] implementam a propriedade de <xref:System.Data.IDbCommand.CommandText%2A> ou fornecem construtores esse conjunto a propriedade usando um argumento de cadeia de caracteres.  
  
-   <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> e <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> e <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>  
  
-   <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> e <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>  
  
-   [System.Data.SqlServerCe.SqlCeCommand](assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&autoUpgrade=True) e [System.Data.SqlServerCe.SqlCeDataAdapter](assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&autoUpgrade=True)  
  
-   <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> e <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>  
  
 Observe que esta regra for violada quando o método ToString de um tipo é usado para construir explicitamente ou implicitamente a cadeia de caracteres da consulta.  A seguir temos um exemplo.  
  
```  
int x = 10;  
string query = "SELECT TOP " + x.ToString() + " FROM Table";  
```  
  
 A regra é violada como um usuário mal\-intencionado pode substituir o método de ToString\(\) .  
  
 A regra é violada também quando ToString é usado implicitamente.  
  
```  
int x = 10;  
string query = String.Format("SELECT TOP {0} FROM Table", x);  
```  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, use uma consulta parametrizada.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se o texto do comando não contém nenhuma entrada do usuário.  
  
## Exemplo  
 O exemplo a seguir mostra um método, `UnsafeQuery`, que viola a regra e um método, `SaferQuery`, que obedece à regra usando uma cadeia de caracteres de comando com parâmetros.  
  
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/VisualBasic/ca2100-review-sql-queries-for-security-vulnerabilities_1.vb)]
 [!code-cs[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CSharp/ca2100-review-sql-queries-for-security-vulnerabilities_1.cs)]
 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../code-quality/codesnippet/CPP/ca2100-review-sql-queries-for-security-vulnerabilities_1.cpp)]  
  
## Consulte também  
 [Visão geral da segurança](../Topic/Security%20Overview2.md)
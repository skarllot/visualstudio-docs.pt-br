---
title: "Como gerenciar arquivos de dados locais no projeto | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.LocalConnectionConverter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Arquivos .mdb"
  - "Arquivos .mdf"
  - "dados [Visual Studio], local"
  - "dados locais"
  - "arquivos mdb"
  - "arquivos mdf"
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como gerenciar arquivos de dados locais no projeto
Um arquivo de banco de dados local pode ser incluído como um arquivo em um projeto. Na primeira vez que você se conectar a um arquivo de banco de dados local, você pode optar por criar uma cópia de seu projeto ou conecte\-se ao arquivo existente em seu local atual. Se você se conectar ao arquivo existente, ele é deixado no local original. Se você optar por copiar o arquivo no seu projeto, o Visual Studio cria uma cópia dele, adiciona\-o ao seu projeto e modifica a conexão para apontar para a cópia. Outras conexões, como aqueles no Gerenciador de servidores também são modificadas.  
  
 A configuração padrão da propriedade depende do tipo de arquivo de banco de dados que você está usando. O comportamento do **Copy to Output Directory** propriedade não se aplica a Web ou projetos C\+\+.  
  
 Durante o desenvolvimento, talvez você queira exibir os efeitos do código no banco de dados sem fazer essas alterações permanentes. Você pode fazer isso pela configuração do **Copy to Output Directory** propriedade do arquivo como true. Cada vez que as compilações do projeto ou você pressiona F5, o arquivo é copiado para a pasta bin e forem feitas alterações nesse arquivo, não para o arquivo na pasta raiz do seu projeto. O arquivo de banco de dados na sua pasta raiz do projeto é alterado ao editar o esquema de banco de dados ou dados usando **Server Explorer**, **Database Explorer** ou em outra janela de ferramenta.  
  
 A tabela a seguir descreve as configurações do **Copy to Output Directory** propriedade.  
  
|Configuração|Comportamento|  
|------------------|-------------------|  
|**Copiar se mais recente** \(padrão para arquivos. sdf\)|O arquivo de banco de dados é copiado do diretório do projeto para o **bin** diretório na primeira hora que o projeto é compilado. Cada vez subseqüente que você cria o projeto, o **Data de modificação** propriedade dos arquivos é comparada. Se o arquivo na pasta de projeto for mais recente, ele é copiado para o **bin** pasta, substituindo o arquivo que está lá. Se o arquivo no **bin** pasta é mais recente, nenhum arquivo é copiado. Essa configuração persiste quaisquer alterações feitas aos dados durante o tempo de execução, que significa que sempre que você executa o aplicativo e salva as alterações dos dados, essas alterações são visíveis na próxima vez que você executar o aplicativo. **Caution:**  Não recomendamos essa opção para arquivos. mdb ou. mdf. O arquivo de banco de dados pode alterar mesmo quando nenhuma alteração é feita nos dados. Simplesmente abrindo uma conexão em um arquivo de dados \(por exemplo, expandindo o **tabelas** nó **Server Explorer**\) pode marcá\-lo como mais recente.|  
|**Copiar sempre** \(padrão para arquivos. mdf e.\)|O arquivo de banco de dados é copiado do diretório do projeto para o diretório \/bin sempre que você criar seu aplicativo. Portanto, se você cria seu aplicativo e salva as alterações para o arquivo no diretório \/bin, essas alterações serão sobrescritas na próxima vez que o arquivo original é copiado para o diretório \/bin.|  
|**Não copiar**|O arquivo nunca é copiado ou substituído pelo sistema do projeto. Você deve copiar manualmente o arquivo do diretório do projeto para o diretório de saída se você usar essa configuração.|  
  
## Procedimento  
  
#### Para responder a caixa de diálogo de arquivo de banco de dados Local  
  
-   Clique em **Sim** se desejar que o Visual Studio copie o arquivo de banco de dados em seu projeto e modificar a conexão para apontar para a cópia em seu projeto. Para obter mais informações sobre como trabalhar com arquivos de banco de dados em seu projeto, consulte [Visão geral de dados local](../data-tools/local-data-overview.md).  
  
-   Clique em **não** se não quiser que o Visual Studio copie o arquivo de banco de dados em seu projeto. Em vez disso, os pontos de conexão para o arquivo no local original e o arquivo de banco de dados não é adicionada como um arquivo ao projeto.  
  
## Consulte também  
 [Instruções passo a passo: conectando a dados em um arquivo de banco de dados local \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20a%20Local%20Database%20File%20\(Windows%20Forms\).md)   
 [Instruções passo a passo: conectando a dados em um banco de dados do Access \(Windows Forms\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)
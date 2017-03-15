---
title: "Como incluir um arquivo de dados em um aplicativo ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implantação ClickOnce, dados"
  - "acesso a dados, Aplicativos ClickOnce"
  - "implantando aplicativos [ClickOnce], arquivos de dados"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como incluir um arquivo de dados em um aplicativo ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cada [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo instalar é atribuído a um diretório de dados no disco de local do computador de destino onde o aplicativo pode gerenciar seus próprios dados.  Os arquivos de dados podem incluir arquivos de qualquer tipo: arquivos de texto, arquivos XML ou até mesmo arquivos de banco de dados \(. mdb\) do Microsoft Access.  Os procedimentos a seguir mostram como adicionar um arquivo de dados de qualquer tipo em seu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.  
  
### Para incluir um arquivo de dados usando o Mage  
  
1.  Adicione o arquivo de dados ao seu diretório de aplicativo com o restante dos arquivos do seu aplicativo.  
  
     Normalmente, o diretório do aplicativo será um diretório rotulado com a versão atual da implantação — por exemplo, v 1.0.0.0.  
  
2.  Atualize seu manifesto de aplicativo à lista o arquivo de dados.  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     Para executar essa tarefa recria a lista de arquivos em seu manifesto de aplicativo e também gera automaticamente as assinaturas de hash.  
  
3.  Abra o manifesto do aplicativo em seu texto preferencial ou o editor de XML e localize o `file` elemento para o arquivo adicionado recentemente.  
  
     Se você adicionou um arquivo XML denominado `Data.xml`, o arquivo terá uma aparência semelhante ao exemplo de código a seguir.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Adicione o atributo `type` a esse elemento e forneça\-lo com um valor de `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Assinar novamente o manifesto do aplicativo usando o par de chaves ou certificados e, em seguida, assinar novamente o manifesto de implantação.  
  
     Você deve assinar novamente o manifesto de implantação porque seu hash do manifesto do aplicativo foi alterado.  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### Para incluir um arquivo de dados usando o MageUI.exe  
  
1.  Adicione o arquivo de dados ao seu diretório de aplicativo com o restante dos arquivos do seu aplicativo.  
  
2.  Normalmente, o diretório do aplicativo será um diretório rotulado com a versão atual da implantação — por exemplo, v 1.0.0.0.  
  
3.  Sobre o  **arquivo** menu, clique em  **Abrir** para abrir o manifesto do aplicativo.  
  
4.  Selecione o  **arquivos** guia.  
  
5.  Na caixa de texto na parte superior da guia, insira o diretório que contém os arquivos do aplicativo e, em seguida, clique em  **popular**.  
  
     O arquivo de dados será exibida na grade.  
  
6.  Definir o  **Tipo de arquivo** o valor do arquivo de dados para  **dados**.  
  
7.  Salve o manifesto do aplicativo e, em seguida, assinar novamente o arquivo.  
  
     MageUI.exe solicitará que você assinar novamente o arquivo.  
  
8.  Assinar novamente o manifesto de implantação  
  
     Você deve assinar novamente o manifesto de implantação porque seu hash do manifesto do aplicativo foi alterado.  
  
## Consulte também  
 [Acessando dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
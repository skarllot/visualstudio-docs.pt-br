---
title: "N&#227;o &#233; poss&#237;vel iniciar o aplicativo. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.0x800A0001"
  - "vs.message.VB_E_IDACANTBOOT"
ms.assetid: ffc123a0-99e1-4e9d-8f6e-34aa357bf98f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o &#233; poss&#237;vel iniciar o aplicativo.
Um erro inesperado impediu o Visual Studio seja iniciado. Este erro ocorre quando ocorre um dos seguintes itens:  
  
-   O ambiente de desenvolvimento integrado \(IDE\) não pôde carregar MSXML3. dll.  
  
-   O IDE não pôde carregar Mso. dll.  
  
-   O IDE não foi possível carregar DTE.olb.  
  
-   A chave de licença para o Visual Studio não foi criada durante a instalação.  
  
-   O bloqueio de scripts está ativado e não permitir que o código para execução de script.  
  
-   Falha na instalação do .NET Framework, um componente necessário pelo Visual Studio gerar uma imagem nativa válida para mscorlib. dll.  
  
-   O vírus Klez está presente no seu computador.  
  
 Use os procedimentos a seguir para corrigir esse erro.  
  
> [!WARNING]
>  Algumas dessas soluções exigem que você modificar a chave do registro. Se você usar o Editor do Registro incorretamente, poderá causar sérios problemas que podem exigir a reinstalação do sistema operacional. A Microsoft não garante que você conseguirá resolver os problemas resultantes do uso incorreto do Editor do registro. Use o Editor do registro por seu próprio risco.  
  
 O IDE não pôde carregar MSXML3. dll.  
 Julho de 2001 a versão Beta da visualização de tecnologia do MSXML 4.0 deixou o computador em um estado que causa esse comportamento. Para reparar o registro Msxml3. dll, siga estas etapas:  
  
### Desinstalar o Msxml4. dll  
  
1.  Do **Iniciar** menu, escolha **executar**.  
  
2.  No **Abrir** caixa de texto, digite `regsvr32 /u c:\winnt\system32\msxml4.dll` e clique em **OK**.  
  
### Baixe e instale a atualização de segurança para o MSXML  
  
1.  Baixe a atualização de segurança mais recente para a versão do MSXML tem no seu computador de [http:\/\/www.microsoft.com\/windows\/ie\/downloads\/critical\/q317244\/download.asp](http://www.microsoft.com/windows/ie/downloads/critical/q317244/download.asp).  
  
2.  Execute o .exe para a atualização de segurança.  
  
### Baixe e aplique valores atualizados do registro  
  
1.  Baixe os valores de registro atualizado de [http:\/\/download.microsoft.com\/download\/VisualStudioNET\/fix\/1.0\/WIN98MeXP\/Fixxml4.exe](http://download.microsoft.com/download/VisualStudioNET/fix/1.0/WIN98MeXP/Fixxml4.exe).  
  
2.  Clique duas vezes em fixxml4.exe e descompacte os arquivos.  
  
3.  Localize Fixxml4.reg e clique duas vezes no arquivo para atualizar os valores do registro.  
  
 O IDE não pôde carregar Mso. dll.  
 Use a lista a seguir para corrigir problemas com Mso. dll.  
  
### Microsoft Office  
  
-   Desinstale todas as versões Beta do Microsoft Office XP no seu computador.  
  
-   Repare o Office XP por meio de adicionar ou remover programas.  
  
-   No Editor do registro, verifique se a seguinte chave do registro:  
  
     `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0\Path] "MSO"="C:\Program Files\Common Files\Microsoft Shared\Office10\MSO.DLL"`  
  
 O IDE não foi possível carregar DTE.olb.  
 Para corrigir esse erro:  
  
### Registrar Dte.olb  
  
1.  Do **Iniciar** menu, escolha **executar**.  
  
2.  No **Abrir** caixa de texto, digite `regsvr32 C:\Program Files\Common Files\Microsoft Shared\MSEnv\DTE.OLB` e clique em **OK**.  
  
 A chave de licença para o Visual Studio não foi criada durante a instalação.  
 Se a tela inicial para o Visual Studio não contém uma lista de produtos instalados e não inclui informações sobre a pessoa que instalou o produto, a chave de licença está ausente. Além disso, se o Visual Studio não estiver listado na caixa de diálogo Adicionar\/remover programas, a chave de licença está ausente.  
  
 Para corrigir esse problema:  
  
### Criar uma chave de licença para o Visual Studio  
  
-   Remover completamente o Visual Studio do computador e reinstale o produto.  
  
 O bloqueio de scripts está ativado e não permitir que o código para execução de script.  
 Se um aplicativo de terceiros tiver habilitado o bloqueio de scripts, o IDE aparecem e desaparecem.  
  
-   Para corrigir esse problema, verifique se o recurso de bloqueio de script está funcionando corretamente.  
  
 Falha na instalação do .NET Framework, um componente necessário pelo Visual Studio gerar uma imagem nativa válida para mscorlib. dll.  
 Se a tela inicial para o Visual Studio aparece rapidamente e, em seguida, desaparece, talvez você não tenha uma imagem nativa válida para o arquivo mscorlib. dll. Esse arquivo é criado durante a instalação do .NET Framework no diretório \\%windir%\\assembly\\NativeImages1\_v1.0.3705\\mscorlib.  
  
 Para corrigir esse problema:  
  
### Criar um arquivo válido de mscorlib. dll  
  
1.  Desinstale e reinstale o .NET Framework.  
  
 O vírus Klez está presente no seu computador.  
 Se seu computador está infectado com o vírus Klez, o erro "o aplicativo não pode iniciar." poderá ser exibido. É recomendável que você atualize seu software antivírus e, em seguida, varredura de vírus no computador.
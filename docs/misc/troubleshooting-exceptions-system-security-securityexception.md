---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Security.SecurityException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHSecurity"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe System.Security.SecurityException"
  - "Classe SecurityException"
ms.assetid: 7679ef74-dd15-439f-bfeb-0fb45f8b2373
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Security.SecurityException
Um <xref:System.Security.SecurityException> exceção é lançada quando é detectado um erro de segurança.  
  
## Dicas associadas  
 Ajuste o nível de permissão do assembly usando a página de propriedades.  
 Para obter mais informações, consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.SqlPermissionLevel%2A>.  
  
 Armazenar dados de aplicativo no armazenamento isolado.  
 Armazenamento isolado é um armazenamento de dados que fornece isolamento e segurança ao definir maneiras padronizadas de associar códigos com dados salvos. Para obter mais informações, [Armazenamento isolado](../Topic/Isolated%20Storage.md).  
  
 Se usando <xref:System.Windows.Forms.OpenFileDialog> , use o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método para abrir ou salvar um arquivo.  
 Isso permite que o aplicativo para executar em uma situação de confiança parcial.  
  
 Verifique se o aplicativo está lendo e gravando em logs de eventos existentes no computador local.  
 O aplicativo pode não ter permissões suficientes para criar logs ou gravar em computadores não locais.  
  
 Se chamando bibliotecas não gerenciadas, use bibliotecas gerenciadas equivalentes.  
 Uma API equivalente pode existir no Framework. Para obter mais informações, consulte [Solucionando problemas de interoperabilidade](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability).  
  
 Use janelas seguras.  
 O <xref:System.Security.Permissions.UIPermissionWindow> enumeração Especifica o tipo de janela que código tem permissão para usar.  
  
 Permitir que os usuários por meio de <xref:System.Windows.Forms.PrintDialog> componente.  
 Isso permite que o aplicativo para executar em uma situação de confiança parcial. Para obter mais informações, consulte <xref:System.Windows.Forms.PrintDialog>.  
  
 Imprimir na impressora padrão.  
 Isso permite que o aplicativo para executar em uma situação de confiança parcial. Você pode estar tentando acessar uma impressora à qual você não tem direitos.  
  
 Recupere dados do mesmo servidor Web do qual ele foi implantado.  
 Isso permite que o aplicativo para executar em uma situação de confiança parcial.  
  
 Ao implantar uma solução Office, verifique se que você cumpriu todos os requisitos de segurança necessários.  
 Para obter mais informações, consulte [Considerações sobre segurança específicas para soluções do Office](/office-dev/office-dev/specific-security-considerations-for-office-solutions).  
  
 Se um assembly que implementa o objeto de segurança personalizado fizer referência a outros assemblies, adicione os assemblies referenciados à lista de assemblies de confiança total.  
 Para obter mais informações, consulte [Caspol.exe \(Ferramenta de Política de Segurança de Acesso de Código\)](../Topic/Caspol.exe%20\(Code%20Access%20Security%20Policy%20Tool\).md).  
  
## Consulte também  
 <xref:System.Security.SecurityException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
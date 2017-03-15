---
title: "Adi&#231;&#227;o de servi&#231;os da Web para sistemas de projeto | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sistemas de projeto, adicionando a serviços da Web"
  - "Serviços da Web, adicionando a sistemas de projeto de VSPackage"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Adi&#231;&#227;o de servi&#231;os da Web para sistemas de projeto
XML Web services são, em geral, recursos URL endereçável que retornam informações de programação para o sistema do projeto usando o protocolo SOAP \(Simple Object Access Protocol\).  Você pode integrar os serviços da Web ao seu sistema de projeto VSPackage usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> interface.  
  
### Para adicionar um serviço da Web ao seu sistema de projeto  
  
1.  Chame `QueryService` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> por meio da interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> service.  
  
2.  Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>.  Se você passar `pDiscoverySession` parâmetro como `NULL`, uma sessão de detecção é criada para você e a sessão é armazenado em cache para que ele esteja disponível para uso subseqüente pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> interface.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>método retorna um ponteiro para <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>.  Passar o objeto de automação para a pasta de referências de serviço da Web como o `pUnkWebReferenceFolder` parâmetro.  O ambiente de Visual Studio, em seguida, verifica se o serviço da Web já está presente.  Se o serviço da Web não estiver presente, o ambiente de baixa e adiciona o serviço da Web a uma pasta e quaisquer arquivos adicionais \(como arquivos. WSDL\) a nós filho da pasta.  
  
## Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
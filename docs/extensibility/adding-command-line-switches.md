---
title: "Adicionando opções de linha de comando | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6327d5c9d1ca2074e93e502c061ba7c0c991f4be
ms.lasthandoff: 02/22/2017

---
# <a name="adding-command-line-switches"></a>Adicionando opções de linha de comando
Você pode adicionar opções de linha de comando que se aplicam ao seu VSPackage quando devenv.exe é executado. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute>para declarar o nome do comutador e suas propriedades.</xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> Neste exemplo, a opção MySwitch é adicionada para uma subclasse de VSPackage chamado **AddCommandSwitchPackage** sem argumentos e com o VSPackage carregados automaticamente.  
  
```c#  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Os parâmetros nomeados são mostrados na tabela a seguir  
  
 Arguments  
 O número de argumentos para o comutador. Pode ser "*", ou uma lista de argumentos.  
  
 DemandLoad  
 Carrega o VSPackage automaticamente se for definido como 1, caso contrário, defina como 0.  
  
 HelpString  
 A cadeia de caracteres ou recurso ID da Ajuda da cadeia de caracteres para exibir com **devenv /?**.  
  
 Nome  
 O comutador.  
  
 PackageGuid  
 O GUID do pacote.  
  
 O primeiro valor de argumentos geralmente é 0 ou 1. Um valor especial ' *' pode ser usado para indicar que o resto inteiro de linha de comando é o argumento. Isso pode ser útil para cenários em que um usuário deve passar uma cadeia de caracteres de comando do depurador de depuração.  
  
 O valor de DemandLoad é `true` (1) ou `false` (0) indica que o VSPackage deve ser carregado automaticamente.  
  
 O valor de HelpString é a ID de recurso da cadeia de caracteres que aparece no devenv /? Exibição de Ajuda. Esse valor deve estar no formato "#nnn" onde nnn é um inteiro. O valor de cadeia de caracteres no arquivo de recurso deve terminar com um caractere de nova linha.  
  
 O valor do nome é o nome do comutador.  
  
 O valor de PackageGuid é o GUID do pacote que implementa essa opção. O IDE usa esse GUID para encontrar o VSPackage no registro ao qual se aplica a opção de linha de comando.  
  
## <a name="retrieving-command-line-switches"></a>Recuperando opções de linha de comando  
 Quando o pacote é carregado, você pode recuperar as opções de linha de comando, executando as etapas a seguir.  
  
1.  Em seu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>implementação, chamada `QueryService` em <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine>para obter o <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> </xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>  
  
2.  Chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>para recuperar as opções de linha de comando que o usuário inseriu.</xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A>  
  
 O código a seguir mostra como descobrir se a opção de linha de comando MySwitch foi inserida pelo usuário:  
  
```c#  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 É sua responsabilidade verificar as opções de linha de comando sempre que o pacote é carregado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine></xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Opções de linha de comando devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilitário de CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [. Arquivos de Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

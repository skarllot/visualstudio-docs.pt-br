---
title: "Isolar os parâmetros de ponto de entrada do Shell (C++) | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], isolated mode, Start entry point
- Visual Studio shell, isolated mode, Start entry point
ms.assetid: 18f4b18b-2173-4afa-ba0a-42fe33e61118
caps.latest.revision: 10
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
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 13f05a147f0d9ab36d49b93cc91bcbaa7b002c70
ms.lasthandoff: 02/22/2017

---
# <a name="isolated-shell-entry-point-parameters-c"></a>Parâmetros de ponto de entrada do Shell isolado (C++)
Quando um aplicativo baseado no shell do Visual Studio é iniciado, ele chama o ponto de entrada inicial do shell do Visual Studio. As configurações a seguir podem ser substituídas na chamada para o ponto de entrada de inicialização do shell. Para obter uma descrição de cada configuração, consulte [. Arquivos de Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md).  
  
-   AddinsAllowed  
  
-   AllowsDroppedFilesOnMainWindow  
  
-   Nome do aplicativo  
  
-   CommandLineLogo  
  
-   DefaultHomePage  
  
-   DefaultProjectsLocation  
  
-   DefaultSearchPage  
  
-   DefaultUserFilesFolderRoot  
  
-   DisableOutputWindow  
  
-   HideMiscellaneousFilesByDefault  
  
-   HideSolutionConcept  
  
-   NewProjDlgInstalledTemplatesHdr  
  
-   NewProjDlgSlnTreeNodeTitle  
  
-   SolutionFileCreatorIdentifier  
  
-   SolutionFileExt  
  
-   UserFilesSubFolderName  
  
-   UserOptsFileExt  
  
 O modelo Visual Studio Shell isolado cria um arquivo de origem *solutionName*. cpp, onde *solutionName* é o nome da solução para o aplicativo. Esse arquivo define o ponto de entrada principal para o aplicativo, a função _tWinMain. Essa função invoca o ponto de entrada de inicialização do shell.  
  
 Você pode alterar o comportamento do aplicativo alterando essas configurações quando o aplicativo for iniciado.  
  
## <a name="parameters"></a>Parâmetros  
 O ponto de entrada inicial do shell do Visual Studio define cinco parâmetros. Não altere os primeiros quatro parâmetros. O quinto parâmetro usa uma lista de substituição de configurações. O ponto de entrada de inicialização do shell é chamado de ponto de entrada principal de um aplicativo.  
  
 O ponto de entrada de inicialização do shell tem a seguinte assinatura.  
  
```  
typedef int (__cdecl *STARTFCN)(LPSTR, LPWSTR, int, GUID *, WCHAR *pszSettings);  
```  
  
 Se você não deseja substituir as configurações de aplicativo, deixe o valor das configurações substituem o parâmetro como um ponteiro nulo.  
  
 Para substituir uma ou mais configurações, passe uma cadeia de caracteres Unicode que contém as configurações a ser substituído. A cadeia de caracteres é uma lista separada por vírgulas de pares nome-valor. Cada par contém o nome da configuração para substituir, seguido por um sinal de igual (=), seguido do valor para aplicar a configuração.  
  
> [!NOTE]
>  Não inclua espaços em branco em cadeias de caracteres de Unicode.  
  
 Para configurações de Boolianas, as cadeias de caracteres a seguir representam o valor true; todas as outras cadeias de caracteres que representam o valor false. Essas cadeias de caracteres diferenciam maiusculas de minúsculas.  
  
-   \+  
  
-   1  
  
-   -1  
  
-   em  
  
-   true  
  
-   sim  
  
## <a name="example"></a>Exemplo  
 Para desabilitar suplementos e alterar o local padrão dos projetos para seu aplicativo, você pode definir o último parâmetro para "AddinsAllowed=false;DefaultProjectsLocation=%USERPROFILE%\temp".  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando o Shell isolado](../extensibility/customizing-the-isolated-shell.md)   
 [. Arquivos de Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)

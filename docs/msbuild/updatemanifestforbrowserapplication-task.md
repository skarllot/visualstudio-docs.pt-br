---
title: "Tarefa UpdateManifestForBrowserApplication | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "adicionando o elemento <hostInBrowser /> ao manifesto do aplicativo [WPF MSBuild]"
  - "compilando projetos XBAP [WPF MSBuild]"
  - "Tarefa UpdateManifestForBrowserApplication [WPF MSBuild]"
  - "Tarefa UpdateManifestForBrowserApplication [WPF MSBuild], parâmetros"
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa UpdateManifestForBrowserApplication
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> tarefa é executada para adicionar o **\< hostInBrowser \/ \>** elemento para o manifesto do aplicativo \(*projectname*. manifest\) quando um [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] projeto é criado.  
  
## Parâmetros de tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`ApplicationManifest`|Necessário **\[ITaskItem\]** parâmetro.<br /><br /> Especifica o caminho e nome do arquivo de manifesto do aplicativo que você deseja adicionar o `<hostInBrowser />` elemento.|  
|`HostInBrowser`|Necessário **Boolean** parâmetro.<br /><br /> Especifica se deseja modificar o manifesto do aplicativo para incluir o **\< hostInBrowser \/ \>** elemento.  Se **true**, um novo `<`**hostInBrowser \/ \>** elemento é incluído no **\< entryPoint \/ \>** elemento.  Observe que o elemento inclusão é cumulativo: se um **\< hostInBrowser \/ \>** elemento já existir, ele não foi removido ou substituído.  Em vez disso, adicional **\< hostInBrowser \/ \>** elemento é criado.  Se **false**, o manifesto do aplicativo não é modificado.|  
  
## Comentários  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] executar usando [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] implantação e, portanto, deve por publicados com manifestos de implantação e o aplicativo de suporte.  [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] usa o [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) tarefas para gerar um manifesto de aplicativo.  
  
 Em seguida, para configurar um aplicativo para ser hospedado em um navegador, um elemento adicional, **\< hostInBrowser \/ \>** deve ser adicionado ao manifesto do aplicativo, como mostrado no exemplo a seguir:  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 O <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> tarefa é executada quando um [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] projeto é compilado para adicionar o `<hostInBrowser />` elemento.  
  
## Exemplo  
 O exemplo a seguir mostra como garantir que o `<hostInBrowser />` elemento é incluído em um arquivo de manifesto do aplicativo.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Visão geral dos aplicativos de navegador XAML do WPF](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)
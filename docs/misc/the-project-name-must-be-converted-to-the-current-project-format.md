---
title: "O projeto &lt; nome &gt; deve ser convertido para o formato de projeto atual. | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.Conversion7"
  - "vs.UpgradeWarningDlg"
ms.assetid: e27d58e5-c270-468b-bb98-3163d40900bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# O projeto &lt; nome &gt; deve ser convertido para o formato de projeto atual.
Você abriu um projeto que foi criado em uma versão anterior do Visual Studio. Arquivos de projeto devem ser convertidos para formatos atuais antes de um projeto pode ser aberto e editado na versão do Visual Studio instaladas no seu computador. Você pode escolher se deseja ou não converter este projeto agora. As conversões de formato não podem ser desfeitas.  
  
> [!CAUTION]
>  Se o projeto está armazenado sob controle do código fonte e você pretende verificar convertido projeto novamente, verifique primeiro se nenhuma outra solução compartilhá\-lo. Não verifica em um projeto recém\-convertido que ainda está sendo usado em outras soluções não convertidas. Isso será quebrar as dependências dentro dessas soluções e mantê\-los de abrir ou criar corretamente.  
  
 Talvez você queira fazer cópias de backup de seus arquivos de projeto antes de convertê\-los.  
  
> [!NOTE]
>  Como determinados tipos de projeto são convertidos, por exemplo projetos do Visual C\+\+, os arquivos de projeto anterior são marcados com a extensão de arquivo ". old" e salvo no diretório do projeto.  
  
 Projetos somente leitura não são convertidos. Esses projetos só podem ser convertidos por usuários que têm permissão para editá\-los. Antes de um projeto pode ser usado em uma solução convertida, seus arquivos de projeto devem ser convertidos para formatos atuais. Após a conversão de um projeto, você pode não editar, compilar ou executar qualquer solução que inclui o projeto em versões anteriores do Visual Studio.  
  
### Para responder a esta mensagem  
  
1.  Selecione **Sim** ou **não**.  
  
    -   **Sim** \-se o projeto for editável, ele é convertido para o formato usado pela versão do Visual Studio instaladas no seu computador. Se o projeto convertido é armazenado sob controle do código fonte, é extraído em sua unidade local e aberto para edição.  
  
    -   **Não** \-não é convertido, não check\-out do controle do código fonte e não abrir o projeto.  
  
 Se você fizer parte de uma equipe de desenvolvimento, qualquer pessoa que está trabalhando em um projeto deve ter a mesma versão do Visual Studio instalado em suas máquinas locais. Para garantir que seu projeto permaneça acessível, se comunicam regularmente com sua equipe.  
  
## Consulte também  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/pt-br/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compilando aplicativos no Visual Studio](../ide/compiling-and-building-in-visual-studio.md)
---
title: "Falha na convers&#227;o de um ou mais projetos. Esses projetos agora s&#227;o descarregados e marcados como n&#227;o dispon&#237;veis no Gerenciador de solu&#231;&#245;es. Recarregue os projetos para determinar a causa. | Microsoft Docs"
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
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Falha na convers&#227;o de um ou mais projetos. Esses projetos agora s&#227;o descarregados e marcados como n&#227;o dispon&#237;veis no Gerenciador de solu&#231;&#245;es. Recarregue os projetos para determinar a causa.
Você tentou abrir uma solução que contém um ou mais projetos que foram criados em uma versão anterior do Visual Studio. Determinados projetos não pôde ser convertidos e serão marcados como \(não disponível\) no Gerenciador de soluções. Esses projetos devem ser convertidos para formatos atuais antes de sua solução pode ser aberta e editada e reparados projetos podem ser usados na versão do Visual Studio instaladas no seu computador.  
  
### Para responder a esta mensagem  
  
1.  Selecione **Sim** para fechar a caixa de diálogo.  
  
     Projetos que não puderam ser convertidos são marcados **\(não disponível\)** no Gerenciador de soluções.  
  
2.  Recarregue os projetos que não pôde ser convertidos.  
  
    1.  No Solution Explorer, selecione cada projeto na solução ativa que está marcado como **\(não disponível\)**.  
  
    2.  Sobre o **projeto** menu, escolha **Recarregar projeto**.  
  
3.  Examine cuidadosamente quaisquer mensagens de erro que exibem informações sobre problemas com projetos. Problemas possíveis incluem:  
  
    1.  Projeto é somente leitura. Projetos somente leitura não são convertidos. Esses projetos podem ser convertidos somente pelos usuários que têm permissão para editá\-los.  
  
    2.  Projeto já fez check\-out exclusivamente para outro usuário. Esse usuário deve verificar o projeto novamente antes que o check\-.  
  
    3.  Projeto não pode ser retirado de um servidor de rede. Confirme as condições de rede e tente novamente.  
  
    4.  Projeto está corrompido e deve ser recriado.  
  
4.  O endereço estão indicados de problemas ao tentar recarregar os projetos que foram marcados **\(não disponível\)**.  
  
5.  Reabra e converter esses projetos. Talvez você queira fazer cópias de backup de seus arquivos de projeto antes de convertê\-los.  
  
    > [!NOTE]
    >  Como determinados tipos de projeto são convertidos, por exemplo projetos do Visual C\+\+, os arquivos de projeto anterior são marcados com a extensão de arquivo. old e salvo no diretório do projeto.  
  
 Se você fizer parte de uma equipe de desenvolvimento, qualquer pessoa que está trabalhando em um projeto deve ter a mesma versão do Visual Studio instalado em suas máquinas locais. Para garantir que seu projeto permaneça acessível, se comunicam regularmente com sua equipe.  
  
> [!CAUTION]
>  Se os projetos em sua solução são armazenados sob controle do código fonte e você pretende verificar que os projetos convertidos novamente, primeiro determine se outras soluções compartilham qualquer um desses projetos. Não marque em projetos convertidos que ainda estão sendo usados em soluções não convertidas. Isso será quebrar as dependências dentro dessas soluções e impedir que eles sejam abrindo ou criando corretamente.  
  
## Consulte também  
 [NIB: como: descarregar e recarregar projetos](http://msdn.microsoft.com/pt-br/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/pt-br/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Compilando aplicativos no Visual Studio](../ide/compiling-and-building-in-visual-studio.md)
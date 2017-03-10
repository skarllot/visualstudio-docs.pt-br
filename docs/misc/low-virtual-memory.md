---
title: "Pouca mem&#243;ria virtual | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Pouca mem&#243;ria virtual
Esta mensagem aparece quando a memória virtual é para baixar e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de responder.  No entanto, esse erro não ocorre quando a memória virtual em seu computador é baixa mas em vez quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] está executando fora do espaço de endereço.  Mais comumente, esse erro ocorre em computadores que estão executando os sistemas operacionais de 32 bits, que limitam [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a 2 GB de espaço de endereço.  Quando você trabalha com processos de 32 bits, o aplicativo pode resolver apenas 4 GB de memória \(bit 2^32\).  No entanto, as versões de 32 bits do Windows permitem 2 GB de espaço de endereço virtual de um processo para fins internas \(por exemplo, para trabalhar com a placa gráfica do computador ou outros drivers do sistema\).  Portanto, o processo de 32 bits pode usar somente 2 GB para as finalidades internas.  Os usuários podem definir a opção de \/3GB para garantir que permita apenas o Windows 1 GB para se e forneça 3 GB para o processo.  Na maioria dos casos, o desempenho não diminui com um limite de apenas 1 GB para o Windows.  
  
 Em sistemas que executam versões de 64 bits do Windows, esse erro ocorre porque raramente o processo pode usar todos os 4 GB de espaço endereçavel, e o Windows pode usar endereços de memória de 64 bits para trabalhar com drivers de hardware e do sistema.  No entanto, o uso de memória pode exceder 3 GB ou mesmo 4 GB quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] processa alguns conjuntos de dados.  Para obter mais informações, consulte[Visual Studio: Por que há nenhuma versão de 64 bits? \(no entanto\)](http://go.microsoft.com/fwlink/?LinkId=246307).  
  
 Esse erro geralmente ocorre quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estiver armazenando em cachê grandes quantidades de dados ou de vários processos intensivos memória em execução.  
  
 Os seguintes cenários envolvem armazenar em cachê grandes quantidades de dados, e você geralmente pode corrigi\-los reiniciando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Executando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pela primeira vez após a instalação.  
  
-   Instalando ou desinstalar uma extensão.  
  
-   Escolhendo ou personalizar itens em **Caixa de Ferramentas**.  
  
-   Alterando as configurações de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
-   Permitindo que o sistema entre no modo de modo de espera \(hibernando\) quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estiver aberto.  
  
 Os seguintes cenários exigem grandes quantidades de memória ativo.  Nesses casos, é recomendável executar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] apenas com componentes essenciais instância adicional aberta ou processos de execução um segundo de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Compilando grandes soluções.  
  
-   Trabalhar com grandes documentos XML.  
  
-   Soluções de atualização de uma versão anterior de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Retargeting soluções.  
  
-   Executando [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ao editar o código.  
  
-   Executando IntelliTrace em vários projetos.  
  
 Se essas medidas não impedem o erro, você pode aumentar seu espaço de endereço disponível em um sistema que está executando [!INCLUDE[win7](../debugger/includes/win7_md.md)] se você executar bcedit.exe com a seguinte sintaxe:  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 Este comando aumenta sua alocação de memória virtual de usuário de 2 GB a 3 GB em um sistema de x86\-based.  Se você adiciona a opção de \/3GB, o sistema inteiro pode resolver mais memória e dar a cada aplicativo um maior porcentagem de memória disponível.  
  
> [!NOTE]
>  Você deve executar bcdedit.exe com permissões administrativas.  Se a criptografia de BitLocker é ativada, você deve suspendê\-la, faz a alteração, reinicializa o sistema, e reativa em Bitlocker.  
  
 Mesmo após você aumenta sua alocação de memória virtual a 3 GB, esse erro pode retornar porque qualquer único aplicativo ainda pode usar somente 2 GB de memória virtual.  Se este erro persistir para aparecer, reduz o tamanho da sua solução, e reinicie em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Você pode reduzir a solução qualquer um de refatoração o para remover projetos que são raramente usados ou descarregar os projetos que não são necessários.  Se o erro ocorre quando você cria sua solução, tente construa\-a em um prompt de comando.  
  
## Consulte também  
 [Recursos para solucionar problemas de erros IDE](../ide/reference/resources-for-troubleshooting-integrated-development-environment-errors.md)
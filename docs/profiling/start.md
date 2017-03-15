---
title: Iniciar | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: fe26087dbd02b1cca570869e8fb7d714636ef884

---
# <a name="start"></a>Início
A opção **Start** é uma opção de VSPerfCmd.exe que inicializa o criador de perfil para o método de criação de perfil especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Method`  
 Deve ser uma das seguintes palavras-chave:  
  
-   **TRACE** – especifica o método de instrumentação.  
  
-   **SAMPLE** – especifica o método de amostragem.  
  
-   **COVERAGE** – especifica a cobertura de código.  
  
-   **CONCURRENCY** – especifica o método de contenção de recursos.  
  
## <a name="required-options"></a>Opções obrigatórias  
 A opção **Output** deverá ser especificada quando **Start** for especificada na linha de comando.  
  
 **Output:** `filename`  
 Especifica o nome do arquivo de saída.  
  
## <a name="exclusive-options"></a>Opções Exclusivas  
 As opções a seguir só podem ser usadas com a opção **Start** em uma linha de comando.  
  
 **CrossSession**&#124;**CS**  
 Habilita criação de perfis entre processos. Há suporte para ambos os nomes de opção **CrossSession** e **CS**.  
  
 **User:**[`domain\`]`username`  
 Habilita o acesso do cliente ao monitor por meio da conta especificada.  
  
 **WinCounter:** `Path` [**Automark**:`n`]  
 **WinCounter** especifica um contador de desempenho do Windows para incluir como uma marca no arquivo de dados de criação de perfil. **AutoMark** especifica o intervalo em milissegundos entre as coletas do arquivo de dados.  
  
## <a name="invalid-options"></a>Opções inválidas  
 As opções a seguir não podem ser usadas com a opção **Start** em uma linha de comando.  
  
 **Status**  
 **Status** aplica-se aos processos cujos perfis são criados. Ela lista processos e threads e seu estado de perfil atual (Ligado/Desligado). Por exemplo, se um processo for interrompido, **Status** não indicará isso no relatório. **Status** mostrará se perfil do processo foi criado ou não.  
  
 **Shutdown**[**:**`Timeout`]  
 Desliga o criador de perfil.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como usar a opção **Start** do VSPerfCmd.exe para inicializar o criador de perfil.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Criando perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Criando perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Serviços de Criação de Perfil](../profiling/command-line-profiling-of-services.md)


<!--HONumber=Feb17_HO4-->



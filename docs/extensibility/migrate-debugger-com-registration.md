---
title: Migrar o registro de classe do depurador de 64 bits COM | Documentos do Microsoft
ms.custom: 
ms.date: 11/10/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45cfcee6-7a68-4d4f-b3f6-e2d8a0fa066a
caps.latest.revision: 1
author: gregg-miskelly
ms.author: greggm
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
ms.openlocfilehash: e273f31cb1f43ff79fd9a4ade37d112351dea9b5
ms.lasthandoff: 02/22/2017

---
# <a name="migrate-64-bit-debugger-com-class-registration"></a>Migrar o registro de classe COM de depurador de 64 bits

>**Observação:** esta documentação é preliminar e com base na versão RC do Visual Studio 2017.

Para extensões do depurador que registrar classes COM em HKEY_CLASSES_ROOT (com regasm, regsvr32, ou gravar diretamente no registro) e carregados no msvsmon.exe (o depurador remoto), é possível fornecer esse registro para msvsmon sem precisar gravar em HKEY_CLASSES_ROOT. Isso afeta os avaliadores de expressão de depurador .NET herdados ou mecanismos de depuração que são configurados para carregar no processo de msvsmon.exe.

## <a name="msvsmon-comclass-def"></a>msvsmon-comclass-def

Para usar essa técnica, adicione um arquivo comclass-*.msvsmon-def.json ao lado de msvsmon (InstallDir:\Common7\IDE\Remote Debugger\x64).

Aqui está um exemplo de arquivo de definição de comclass msvsmon que registra um gerenciado e uma classe nativa:

Nome do arquivo: MyCompany.MyExample.msvsmon comclass def.json

```json
{
  "managedCOMClasses": [
    {
      "clsid": "{C9F48B25-36ED-4B22-8210-98BC5BE4D1E7}",
      "assemblyName": "MyCompany.MyAssembly",
      "className": "MyCompany.MyNamespace.MyClass"
    }
  ],
  "nativeCOMClasses": [
    {
      "clsid": "{42A476E9-8FA7-44D5-ADFE-216AD371EEC9}",
      "dllPath": "MyExample.dll"
    }
  ]
}
```


---
title: "Fazendo projetos personalizados com reconhecimento de vers&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
caps.handback.revision: 33
manager: "douge"
---
# Fazendo projetos personalizados com reconhecimento de vers&#227;o
No seu sistema de projeto personalizado, você pode permitir que os projetos desse tipo de carga em várias versões do Visual Studio. Você também pode impedir projetos desse tipo de carregamento em uma versão anterior do Visual Studio. Você também pode habilitar o projeto para se identificar para uma versão posterior, caso o projeto exige o reparo, a conversão ou substituição.  
  
## Permitir projetos a carga em várias versões  
 Você pode modificar a maioria dos projetos que foram criados no [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] com SP1 ou posterior para trabalhar em várias versões.  
  
 Antes de um projeto é carregado, o Visual Studio chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> método para determinar se o projeto pode ser atualizado. Se o projeto pode ser atualizado, o `UpgradeProject_CheckOnly` método define um sinalizador que faz com que uma chamada posterior para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> método para atualizar o projeto. Como incompatíveis projetos não podem ser atualizados, `UpgradeProject_CheckOnly` deverá primeiro verificar compatibilidade do projeto, conforme descrito na seção anterior.  
  
 Você, como o autor de um sistema de projeto, implementar `UpgradeProject_CheckOnly` \(da `IVsProjectUpgradeViaFactory4` interface\) para fornecer aos usuários do seu sistema de projeto com uma verificação de atualização. Quando os usuários abrem um projeto, esse método é chamado para determinar se um projeto deve ser reparado antes que ele seja carregado. Os requisitos de atualização possíveis são enumerados na `VSPUVF_REPAIRFLAGS`, e incluem as seguintes possibilidades:  
  
1.  `SPUVF_PROJECT_NOREPAIR`: Não requer nenhum reparo.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: Torna o projeto compatível com uma versão anterior sem encontram os problemas que você possa ter com as versões anteriores do produto.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: Torna o projeto compatível com versões anteriores, mas com algum risco de problemas que podem ser encontrados nas versões anteriores do produto. Por exemplo, o projeto não será compatível se dependia de diferentes versões do SDK.  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: Torna o projeto incompatível com uma versão anterior.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: Indica que a versão atual não dá suporte a este projeto.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: Indica que não há suporte para este projeto.  
  
> [!NOTE]
>  Para evitar confusão, não combine sinalizadores de atualização, quando você defini\-las. Por exemplo, não crie um status de atualização ambíguo como `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Tipos de projeto podem implementar a função `UpgradeProjectFlavor_CheckOnly` do `IVsProjectFlavorUpgradeViaFactory2` interface. Para tornar essa função de trabalho, o `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` implementação mencionada anteriormente deve chamá\-lo. Essa chamada já foi implementada no sistema de base do projeto Visual Basic ou c\#. O efeito dessa função permite que os tipos de projeto também determinar os requisitos de atualização de um projeto, além de que o sistema de projeto base determinou. A caixa de diálogo de compatibilidade mostra dois requisitos mais graves.  
  
 Quando o Visual Studio executa uma verificação de atualização, ele fornece um agente de log em vez de um valor nulo como nas versões anteriores do Visual Studio. O agente de log permite que os sistemas de projeto e tipos para fornecer informações adicionais que podem ajudar a entender a natureza das alterações que são necessárias para tornar seus projetos antigos carregado corretamente. É recomendável que você use o agente de log para fornecer mais informações em vez de usar as caixas de diálogo. Para obter mais informações, consulte [O agente de atualização](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) mais adiante neste tópico.  
  
 Para implementações de gerenciado, as interfaces de atualização de projeto estão disponíveis no assembly de interoperabilidade Microsoft.VisualStudio.Shell.Interop.11.0.dll.  
  
 O `UpgradeProject` método pode determinar se alterações feitas impediria que o projeto seja carregado em uma versão anterior do Visual Studio. Nesse caso, o método marca o projeto como incompatíveis. Para entender como um projeto é marcado como incompatível, consulte [Marcar um projeto como incompatível](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) anteriormente neste tópico. É recomendável que, depois que essa caixa de diálogo for exibida, marque o projeto como incompatível, chamando o método `IVsAppCompat.BreakAssetCompatibility` diretamente, em vez de chamar primeiro o `IVsAppCompat.AskForUserConsentToBreakAssetCompat` método porque a caixa de diálogo não precisa aparecer duas vezes.  
  
 Aqui está um exemplo para ajudar a resumir a experiência do usuário de compatibilidade. Se um projeto foi criado em uma versão anterior e a versão atual determina que uma atualização é necessária, o Visual Studio exibe uma caixa de diálogo para perguntar ao usuário permissão fazer as alterações. Se o usuário concordar, o projeto é modificado e depois carregado. Se a solução, em seguida, é fechada e reaberta na versão anterior, o projeto um vias atualizado será incompatível e não foram carregados. Se o projeto teve necessário apenas um reparo \(em vez de uma atualização\), o projeto reparado ainda será aberto em ambas as versões.  
  
##  <a name="BKMK_Incompat"></a> Marcar um projeto como incompatível  
 Você pode marcar um projeto como incompatível com versões anteriores do Visual Studio.  Por exemplo, suponha que você crie um projeto que usa um recurso do .NET Framework 4.5. Como este projeto não pode ser criado [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], você pode marcá\-lo como incompatíveis que impeçam que a versão de carregá\-lo.  
  
 O componente que adiciona o recurso incompatível é responsável para marcar o projeto como incompatível. O componente deve ter acesso para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface que representa os projetos de interesse.  
  
#### Para marcar um projeto como incompatíveis  
  
1.  No componente, obter um `IVsAppCompat` interface do serviço global SVsSolution.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  No componente, chame `IVsAppCompat.AskForUserConsentToBreakAssetCompat`, e passe uma matriz de `IVsHierarchy` interfaces que representam os projetos de interesse.  
  
     Esse método tem a seguinte assinatura:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Se você implementar o código, será exibida uma caixa de diálogo de compatibilidade de projeto. O será de caixa de diálogo pede ao usuário permissão marcar especificados todos os projetos como incompatíveis. Se o usuário concorda, `AskForUserConsentToBreakAssetCompat` retorna `S_OK`; caso contrário, `AskForUserConsentToBreakAssetCompat` retorna `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  Em cenários mais comuns, a `IVsHierarchy` matriz conterá apenas um item.  
  
3.  Se `AskForUserConsentToBreakAssetCompat` retorna `S_OK`, o componente faz ou aceita as alterações que quebrem a compatibilidade.  
  
4.  Em seu componente, chamar o `IVsAppCompat.BreakAssetCompatibility` método para cada projeto que você deseja marcar como incompatível. O componente pode definir o valor do parâmetro `lpszMinimumVersion` para uma versão mínima específica em vez de ter o Visual Studio procura a cadeia da versão atual no registro. Essa abordagem minimiza o risco do componente inadvertidamente definindo um valor mais alto no futuro, com base no que é o registro no momento. Se esse valor superior foram definida, o Visual Studio não pôde abrir o projeto.  
  
     Esse método tem a seguinte assinatura:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Se o componente definir `lpszMinimumVersion` como NULL, o `BreakAssetCompatibility` chamadas de método de `IVsAppCompat.GetCurrentDesignTimeCompatVersion` método para obter uma cadeia de caracteres que representa a versão atual do Visual Studio.  
  
     Esse método tem a seguinte assinatura:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Em seguida, chama o método BreakAssetCompatibility o `IVsHierarchy.SetProperty` método para definir a raiz `VSHPROPID_MinimumDesignTimeCompatVersion` propriedade para o valor da cadeia de versão que você obteve na etapa anterior.  
  
     Para obter mais informações, consulte <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Você deve implementar o `VSHPROPID_MinimumDesignTimeCompatVersion` propriedade marcar um projeto como compatível ou incompatível. Por exemplo, se o sistema de projeto usa um arquivo de projeto MSBuild, adicionar ao arquivo de projeto um `<MinimumVisualStudioVersion>` Criar propriedade que tem um valor igual ao correspondente `VSHPROPID_MinimumDesignTimeCompatVersion` valor da propriedade.  
  
## Detectar se um projeto é incompatível  
 Um projeto que é incompatível com a versão atual do Visual Studio deve ser mantido de carregamento. Além disso, um projeto que é incompatível não pode ser atualizado ou reparado. Portanto, um projeto deve ser verificado quanto à compatibilidade duas vezes: primeiro, quando ele é considerado para atualização ou reparo e segundo, antes ele é carregado.  
  
 Para habilitar a detecção de incompatibilidade de projeto, você deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> métodos. Se um projeto é incompatível, `UpgradeProject_CheckOnly` deve retornar o código de êxito `VS_S_INCOMPATIBLEPROJECT`, e `CreateProject` deve retornar o código de erro `VS_E_INCOMPATIBLEPROJECT`. Para projetos de tipo, você deve implementar `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` em vez de `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 Um sistema de projeto é chamado para como tipo se ele tiver uma web, Office \(VSTO\), Silverlight ou outro tipo de projeto criado sobre ele. Sistemas mais antigos do projeto que já implementam `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` e tipo sistemas de projeto que já implementam `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` continuarão a ter suporte. A versão mais antiga do `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` tem a seguinte assinatura de implementação:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly( /* [in] */ BSTR bstrFileName, /* [in] */ IVsUpgradeLogger *pLogger, /* [out] */ BOOL *pUpgradeRequired, /* [out] */ GUID *pguidNewProjectFactory, /* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags )  
```  
  
 Se esse método define `pUpgradeRequired` como TRUE e retornará `S_OK`, o resultado será tratado como "Atualização" e com que o método definir um sinalizador de atualização para o valor `VSPUVF_PROJECT_ONEWAYUPGRADE`, que é descrito posteriormente neste tópico. A seguir retorna valores são suportados usando este método antigo, mas somente quando `pUpgradeRequired` é definida como TRUE:  
  
1.  `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Converte esse valor de retorno de `pUpgradeRequired` valor como verdadeiro como equivalente a `VSPUVF_PROJECT_SAFEREPAIR`, que é descrito posteriormente neste tópico.  
  
2.  `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Converte esse valor de retorno de `pUpgradeRequired` valor como verdadeiro como equivalente a `VSPUVF_PROJECT_UNSAFEREPAIR`, que é descrito neste tópico  
  
3.  `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Converte esse valor de retorno de `pUpgradeRequired` valor como verdadeiro como equivalente a `VSPUVF_PROJECT_ONEWAYUPGRADE`, que é descrito posteriormente neste tópico.  
  
 As novas implementações em `IVsProjectUpgradeViaFactory4` e `IVsProjectFlavorUpgradeViaFactory2` permitem especificar o tipo de migração com mais precisão.  
  
> [!NOTE]
>  Você pode armazenar em cache o resultado da verificação de compatibilidade, o `UpgradeProject_CheckOnly` método para que ele também pode ser usado por uma chamada subsequente para `CreateProject`.  
  
 Por exemplo, se o `UpgradeProject_CheckOnly` e `CreateProject` métodos que são escritos para um [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] com o sistema de projeto do SP1 examinar um arquivo de projeto e descobrir que o `<MinimumVisualStudioVersion>` compilação é "11.0", o Visual Studio 2010 com SP1 não é possível carregar o projeto. Além disso, **solução Navigator** indica que o projeto é "incompatível" e não carregá\-lo.  
  
##  <a name="BKMK_UpgradeLogger"></a> O agente de atualização  
 A chamada para `IVsProjectUpgradeViaFactory::UpgradeProject` contém um `IVsUpgradeLogger` logger, quais sistemas de projeto e tipos deve usar para fornecer rastreamento atualização detalhado para solução de problemas. Se um aviso ou erro é registrado, o Visual Studio mostra o relatório de atualização.  
  
 Quando você grava para o agente de atualização, considere as seguintes diretrizes:  
  
-   Visual Studio chamará Flush após todos os projetos de concluída a atualização. Não chamá\-la em seu sistema de projeto.  
  
-   A função LogMessage tem os seguintes ErrorLevels:  
  
    -   0 é para todas as informações que você deseja rastrear.  
  
    -   1 é para um aviso.  
  
    -   2 é um erro  
  
    -   3 é para o formatador de relatório. Quando o projeto é atualizado, faça a palavra "Convertido" uma vez e não localizar a palavra.  
  
-   Se um projeto não requer nenhum reparo ou atualização, o Visual Studio irá gerar o arquivo de log somente se o sistema de projeto tivesse conectado um aviso ou um erro durante a métodos UpgradeProject\_CheckOnly ou UpgradeProjectFlavor\_CheckOnly.
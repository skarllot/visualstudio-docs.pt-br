---
title: "Como: definir a marca um VSPackage (c# e Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Caixa de diálogo sobre"
  - "VSPackages, telas de abertura"
  - "VSPackages, identidade Visual"
ms.assetid: 705a41c3-63d6-4c1e-9f82-771be9191579
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Como: definir a marca um VSPackage (c# e Visual Basic)
Apareça na  **sobre** caixa de diálogo e a tela de abertura, VSPackages deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> interface.  Isso fornece as seguintes informações para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Nome  
  
-   ID, como o número de série ou de versão  
  
-   Informações  
  
-   Ícone de logotipo  
  
 O código a seguir é de [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
### Para implementar a interface IVsInstalledProduct  
  
1.  Adicionar o <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> de atributo à classe que implementa o VSPackage.  Essa classe deve derivar de ambos <xref:Microsoft.VisualStudio.Shell.Package> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_1.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#1](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_1.vb)]  
  
     O primeiro argumento, <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute.UseInterface%2A>, da <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> atributo o informa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> para obter informações sobre o produto, em vez da chave do registro ' InstalledProducts '.  Os argumentos restantes selecione recursos de seqüência de caracteres para exibir o nome do produto, detalhes e identificação, respectivamente.  No entanto, como o primeiro argumento é `true`, os argumentos restantes são `null`.  
  
2.  Com o botão direito <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>, aponte para  **Implementar Interface**e, em seguida, clique em  **Implementar Interface**.  
  
3.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> usando o código a seguir.  
  
     [!code-cs[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/CSharp/how-to-brand-a-vspackage-csharp-and-visual-basic_2.cs)]
     [!code-vb[VSSDKPackageSplashHelpAboutLoadKey#2](../misc/codesnippet/VisualBasic/how-to-brand-a-vspackage-csharp-and-visual-basic_2.vb)]  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]chamar esses métodos para obter informações para o VSPackage de identificação de marca.  O método GetResourceString é usado para localizar essas informações.  
  
    > [!NOTE]
    >  Comentários de código são excluídos por questões de brevidade.  Você pode encontrá\-los no [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
### Para manter as seqüências de caracteres de informações de produto  
  
1.  Clique duas vezes o arquivo de recurso. resx associado com o VSPackage.  
  
     O editor de recursos é aberta.  
  
2.  Localizar ou adicionar o nome do produto, informações e a identificação.  
  
     As seguintes seqüências de caracteres de recurso a [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
     @101  
     Tela de abertura do pacote e ajuda sobre o nome oficial \(C\#\).  
  
     @102  
     Este pacote demonstra como exibir o texto e imagem na tela de abertura e a Ajuda sobre.  
  
     @104  
     8.0  
  
3.  Selecionar e editar essas informações como você deseja.  
  
### Para manter a ícones de produto e bitmaps  
  
1.  Adicione os ícones e bitmaps ao projeto como recursos do projeto.  
  
     Para obter mais informações, consulte [NOT IN BUILD: Adding and Editing Resources \(Visual C\#\)](http://msdn.microsoft.com/pt-br/95f15d03-bed0-410c-8d1f-dece5199ba1e).  
  
2.  Feche o editor de recursos e reabrir o arquivo. resx em um editor de texto ou XML.  
  
    > [!NOTE]
    >  O editor de recursos não oferece suporte para atribuir identificações de recurso a itens diferentes de seqüências de caracteres.  
  
3.  Localizar ou adicionar os recursos de ícone e o bitmap para o arquivo. resx.  Os recursos a seguir são de [Exemplos VSSDK](../misc/vssdk-samples.md).  
  
    ```  
    <data name="300" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.bmp;System.Drawing.Bitmap, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    <data name="400" type="System.Resources.ResXFileRef, System.Windows.Forms">  
        <value>GenericPackage.ico;System.Drawing.Icon, System.Drawing,  
            Version=2.0.0.0, Culture=neutral,         PublicKeyToken=b03f5f7f11d50a3a</value>  
    </data>  
    ```  
  
### Para testar as telas de abertura e de caixa de diálogo sobre  
  
-   Para testar sua VSPackage, consulte [Como: testar a Ajuda sobre e telas de abertura](../misc/how-to-test-the-help-about-and-splash-screens.md).  
  
## Consulte também  
 [Marca de VSPackage](/visual-cpp/misc/vspackage-branding)
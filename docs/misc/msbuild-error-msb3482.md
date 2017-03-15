---
title: "Erro MSB3482 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.SignFile.SignToolError"
helpviewer_keywords: 
  - "MSB3482"
ms.assetid: fd09371f-2658-4534-affa-edb485575f1a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3482 (MSBuild)
**MSB3482: Ocorreu um erro de assinatura: '\< erro \>'.**  
  
 Quando você publica usando a implantação do ClickOnce ou usando o SignTool para assinar manifestos, você pode encontrar esse erro, que é gerado pelo SignTool. Problemas comuns estão listados aqui.  
  
 **Ocorreu um erro durante a assinatura: ' valor não pode ser nulo. Nome do parâmetro: strongNameKey'.**  
  
 Este erro pode aparecer na lista de erros durante a implantação do ClickOnce. O problema é causado por selecionando uma chave de assinatura inválida. Normalmente, você está tentando usar uma chave que é não\-criptografado RSA. SignTool suporta somente criptografia de chave RSA.  
  
 Para corrigir esse erro, obtenha uma chave de criptografia RSA é habilitado de assinatura de código.  
  
 **Ocorreu um erro durante a assinatura: 'uma cadeia de certificados não pôde ser criada para uma autoridade raiz confiável.'**  
  
 Este erro pode aparecer na lista de erros durante a implantação do ClickOnce. O problema é que o certificado tenha uma autoridade de cadeia ou raiz que não é confiável no computador do usuário. Isso geralmente ocorre ao mover\/chaves de certificados de computador para computador.  
  
 Para corrigir esse erro, instale o "certificado de raiz da autoridade de certificação \(CA\) que o criou. Normalmente, você pode ir para o site do fornecedor da autoridade de certificação e baixá\-lo novamente, conforme necessário.  
  
 **Ocorreu um erro durante a assinatura: ' Falha ao assinar … \\setup.exe. Erro de SignTool: ISignCode::Sign retornou o erro: 0x80880253 do certificado do assinante não é válido para a assinatura.'**  
  
 Este erro pode aparecer na lista de erros durante a implantação do ClickOnce.  
  
 O problema é provavelmente causado pelo certificado não sendo dentro das datas válidas, por exemplo, se você tiver um certificado expirado.  
  
 Para corrigir esse erro, obtenha um certificado atualizado que tem uma data válida.  
  
 Para obter informações sobre como atualizar o certificado, consulte o artigo 925521, "você recebe uma mensagem de erro ao tentar atualizar um Visual Studio 2005 ClickOnce aplicativo após o certificado que was usado para logon o instalação expira" no Microsoft Knowledge Base em [http:\/\/support.microsoft.com](http://support.microsoft.com/kb/925521).  
  
 **Conjunto de chaves não existe.**  
  
 Pode haver uma incompatibilidade entre o arquivo. pfx e o certificado. Tente excluir e reinstalar o certificado e\/ou recriar o arquivo. pfx.  
  
 **chave inválida para uso no estado especificado**  
  
 Consulte http:\/\/blogs.msdn.com\/b\/smondal\/archive\/2012\/05\/08\/an\-error\-occurred\-while\-signing\-key\-not\-valid\-for\-use\-in\-specified\-state.aspx  
  
 **' O parâmetro está incorreto.**  
  
 É que a compilação está em execução em um serviço ou em uma conta de usuário diferente daquele que importou o certificado? Tente desativar as configurações de diretiva de segurança Local que requer proteção de chave privada.  Em seguida, excluir e importe novamente o certificado da conta de usuário da compilação.  
  
 **A operação solicitada não pode ser concluída.  O computador deve ser confiável para delegação e a conta de usuário atual deve ser configurada para permitir a delegação.**  
  
 Consulte [esta postagem de blog do MSDN.](http://technet.microsoft.com/en-us/library/cc782684\(v=ws.10\).aspx)  
  
## Consulte também  
 [Introdução à assinatura de código](https://msdn.microsoft.com/en-us/library/ms537361\(v=vs.85\).aspx)   
 [SignTool.exe \(Ferramenta de Assinatura\)](../Topic/SignTool.exe%20\(Sign%20Tool\).md)   
 [Página de Assinatura, Designer de Projeto](../ide/reference/signing-page-project-designer.md)   
 [Como: assinar um Assembly \(Visual Studio\)](http://msdn.microsoft.com/pt-br/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Como assinar um assembly com um nome forte](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Assemblies de nomes fortes](../Topic/Strong-Named%20Assemblies.md)   
 [Para aplicativos gerenciados de assinatura de nome forte](http://msdn.microsoft.com/pt-br/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)
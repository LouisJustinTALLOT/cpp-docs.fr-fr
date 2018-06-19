---
title: -hotpatch (création d’Image corrigeable en mémoire) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb0f27c8da03104ee3633d9ea1a5f1232407931e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376203"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Créer une image corrigeable en mémoire)
Prépare une image corrigeable en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/hotpatch  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque **/hotpatch** est utilisé dans une compilation, le compilateur garantit que première instruction de chaque fonction est d’au moins deux octets, ce qui est nécessaire pour l’application de correctifs à chaud.  
  
 Pour terminer la préparation de création d’une image corrigeable en mémoire, une fois que vous utilisez **/hotpatch** pour compiler, vous devez utiliser [/FUNCTIONPADMIN (créer une Image corrigeable en mémoire)](../../build/reference/functionpadmin-create-hotpatchable-image.md) à lier. Lorsque vous compilez et liez une image à l’aide d’un appel de cl.exe, **/hotpatch** implique **/functionpadmin**.  
  
 Étant donné que les instructions sont toujours deux octets ou plus sur l’architecture ARM et parce que x64 compilation est toujours traitée comme si **/hotpatch** a été spécifié, vous n’êtes pas obligé de spécifier **/hotpatch** lorsque vous compilez pour ces cibles ; Toutefois, vous devez toujours le lier à l’aide de **/functionpadmin** pour créer des images corrigeables en mémoire pour eux. Le **/hotpatch** du compilateur option uniquement affecte x86 compilation.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Ajoutez l’option du compilateur pour le **des Options supplémentaires** boîte.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="guidance"></a>Conseils  
 Pour plus d’informations sur la gestion des mises à jour, consultez le « Guide de sécurité pour mettre à jour de gestion » à [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
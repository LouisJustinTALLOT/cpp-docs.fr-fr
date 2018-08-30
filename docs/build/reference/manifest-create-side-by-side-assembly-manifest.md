---
title: -MANIFEST (créer un manifeste d’Assembly de côte à côte) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
dev_langs:
- C++
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7cdf0f5d1d736635af3d7bf1a853e9002e072ef5
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43199111"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Créer un manifeste d'assembly côte à côte)
```  
/MANIFEST[:{EMBED[,ID=#]|NO}]  
```  
  
## <a name="remarks"></a>Notes  
 / MANIFESTE spécifie que l’éditeur de liens doit créer un fichier manifeste côte à côte. Pour plus d’informations sur les fichiers manifeste, consultez [référence des fichiers manifeste](/windows/desktop/SbsCs/manifest-files-reference).  
  
 La valeur par défaut est /MANIFEST.  
  
 Le /MANIFEST : incorporer option spécifie que l’éditeur de liens doit incorporer le fichier manifeste dans l’image en tant que ressource de type RT_MANIFEST. Le paramètre facultatif `ID` paramètre est l’ID de ressource à utiliser pour le manifeste. Utilisez la valeur 1 pour un fichier exécutable. Utilisez la valeur 2 pour une DLL pour lui permettre de spécifier les dépendances privés. Si le `ID` paramètre n’est pas spécifié, la valeur par défaut est 2 si l’option /DLL est définie ; sinon, la valeur par défaut est 1.  
  
 À compter de Visual Studio 2008, les fichiers manifeste pour les fichiers exécutables contiennent une section qui spécifie les informations de contrôle de compte utilisateur (UAC). Si vous spécifiez /MANIFEST mais que vous ne spécifiez ni [/MANIFESTUAC](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md) ni [/DLL](../../build/reference/dll-build-a-dll.md), un fragment du contrôle par défaut qui a la valeur de niveau de contrôle de compte utilisateur *asInvoker* est inséré dans le manifeste. Pour plus d’informations sur les niveaux UAC, consultez [/MANIFESTUAC (informations UAC incorpore dans le manifeste)](../../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Pour modifier le comportement par défaut pour le compte d’utilisateur, effectuez l’une d'entre elles :  
  
-   Spécifiez l’option/MANIFESTUAC et définissez le niveau de l’UAC sur la valeur souhaitée.  
  
-   Ou spécifiez l’option : no si vous ne souhaitez pas générer un fragment du contrôle dans le manifeste.  
  
 Si vous ne spécifiez pas /MANIFEST, mais spécifiez [/MANIFESTDEPENDENCY](../../build/reference/manifestdependency-specify-manifest-dependencies.md) des commentaires, un fichier manifest est créé. Un fichier manifest n’est pas créé si vous spécifiez/manifest : no.  
  
 Si vous spécifiez /MANIFEST, le nom du fichier manifeste est la même que le nom de votre fichier de sortie, mais avec l’extension .manifest ajoutée au nom de fichier. Par exemple, si votre nom de fichier de sortie est MyFile.exe, le nom du fichier manifeste est MyFile.exe.manifest.  Si vous spécifiez MANIFESTFILE :*nom*, le nom du manifeste est ce que vous spécifiez dans *nom*.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le nœud **Propriétés de configuration**.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **le fichier manifeste** page de propriétés.  
  
5.  Modifier le **génération d’un manifeste** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
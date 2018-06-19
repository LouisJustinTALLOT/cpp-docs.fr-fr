---
title: -VERSION (informations de Version) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
dev_langs:
- C++
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 092fd11d7bf062afb59c9b33d620624c63b5e01f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378988"
---
# <a name="version-version-information"></a>/VERSION (Informations de version)
```  
/VERSION:major[.minor]  
```  
  
## <a name="remarks"></a>Notes  
 où :  
  
 *principaux*et *secondaire*  
 Le numéro de version dans l’en-tête du fichier .exe ou .dll.  
  
## <a name="remarks"></a>Notes  
 L’option /VERSION indique à l’éditeur de liens pour placer un numéro de version dans l’en-tête du fichier .exe ou .dll. Utilisez DUMPBIN [/HEADERS](../../build/reference/headers.md) pour afficher le champ de version d’image de OPTIONAL HEADER VALUES pour voir le résultat de.  
  
 Le *majeure* et *secondaire* arguments sont des nombres décimaux compris entre 0 et 65 535. La valeur par défaut est la version 0.0.  
  
 Les informations spécifiées avec l’option /VERSION n’affectent pas les informations de version qui s’affiche pour une application lorsque vous affichez ses propriétés dans l’Explorateur de fichiers. Ces informations proviennent d’un fichier de ressources qui est utilisé pour générer l’application. Consultez [Éditeur d’informations sur](../../windows/version-information-editor.md) pour plus d’informations.  
  
 Une autre consiste à insérer un numéro de version avec le [VERSION](../../build/reference/version-c-cpp.md) instruction de définition de module.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **général** page de propriétés.  
  
4.  Modifier la **Version** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
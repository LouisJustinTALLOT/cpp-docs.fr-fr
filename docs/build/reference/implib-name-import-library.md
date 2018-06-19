---
title: -/IMPLIB (nommer la bibliothèque importation) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edc0fcb1b216319d6f6c9924cb92a165b3196b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32375270"
---
# <a name="implib-name-import-library"></a>/IMPLIB (Nommer la bibliothèque d'importation)
  
> /IMPLIB :*nom de fichier*  
  
## <a name="parameters"></a>Paramètres  
  
*filename*  
Nom spécifié par l’utilisateur pour la bibliothèque d’importation. Il remplace le nom par défaut.  
  
## <a name="remarks"></a>Notes  
  
L’option /IMPLIB substitue le nom par défaut pour la bibliothèque d’importation qui crée des liens lorsqu’il génère un programme contenant des exportations. Le nom par défaut est formé du nom de base du fichier de sortie principal et de l’extension. lib. Un programme contient des exportations si un ou plusieurs des opérations suivantes sont spécifiées :  
  
-   Le [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) mot clé dans le code source  
  
-   [EXPORTATIONS](../../build/reference/exports.md) instruction dans un fichier .def  
  
-   Un [/EXPORT](../../build/reference/export-exports-a-function.md) spécification dans une commande LINK  
  
 LINK ignore /IMPLIB lorsqu’une bibliothèque d’importation n’est pas créée. Si aucune exportation n’est spécifiées, le lien ne crée pas une bibliothèque d’importation. Si un fichier d’exportation est utilisé dans la génération, LINK considère qu’une bibliothèque d’importation existe déjà et qu’il ne crée pas une. Pour plus d’informations sur les bibliothèques d’importation et exportation de fichiers, consultez [Référence LIB](../../build/reference/lib-reference.md).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **avancé** page de propriétés.  
  
4.  Modifier la **bibliothèque d’importation** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
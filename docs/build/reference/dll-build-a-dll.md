---
title: -DLL (générer une DLL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1767ac9ef063ace2ee9d567dd9038519afababf8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373073"
---
# <a name="dll-build-a-dll"></a>/DLL (Générer une DLL)
```  
/DLL  
```  
  
## <a name="remarks"></a>Notes  
 L’option /DLL génère une DLL en tant que fichier de sortie principal. Une DLL contient généralement des exportations qui peuvent être utilisées par un autre programme. Il existe trois méthodes de spécification des exportations, répertoriées dans l’ordre d’utilisation recommandé :  
  
1.  [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source  
  
2.  Un [exportations](../../build/reference/exports.md) instruction dans un fichier .def  
  
3.  Un [/EXPORT](../../build/reference/export-exports-a-function.md) spécification dans une commande LINK  
  
 Un programme peut utiliser plusieurs méthodes.  
  
 Une autre consiste à générer une DLL avec la **bibliothèque** instruction de définition de module. Les options /BASE et /DLL réunies sont équivalentes à la **bibliothèque** instruction.  
  
 Ne spécifiez pas cette option dans l’environnement de développement. Cette option est réservée uniquement sur la ligne de commande. Cette option est définie lorsque vous créez un projet DLL avec un Assistant Application.  
  
 Notez que si vous créez votre bibliothèque d’importation dans une étape préliminaire, avant de créer votre fichier .dll, vous devez passer le même jeu de fichiers objets lors de la génération du fichier .dll que vous avez passé lors de la création de la bibliothèque d’importation.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **propriétés de Configuration** dossier.  
  
3.  Cliquez sur le **général** page de propriétés.  
  
4.  Modifier la **Configuration Type** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
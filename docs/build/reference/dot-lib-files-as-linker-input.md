---
title: ". LIB des fichiers en tant qu’entrée de l’éditeur de liens | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs:
- C++
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 181c8c3e5e762f2f20d99ca2acadaf285e717b6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="lib-files-as-linker-input"></a>.Fichiers .lib en tant qu'entrée de l'Éditeur de liens
LINK accepte les bibliothèques standard COFF et COFF bibliothèques d’importation, qui portent généralement l’extension. lib. Les bibliothèques standard contiennent des objets et sont créés par l’outil LIB. Bibliothèques d’importation contiennent des informations sur les exportations dans d’autres programmes et sont créées soit par LINK lorsqu’il génère un programme contenant des exportations, ou par l’outil LIB. Pour plus d’informations sur l’utilisation de LIB pour créer standard ou des bibliothèques d’importation, consultez [Référence LIB](../../build/reference/lib-reference.md). Pour plus d’informations sur l’utilisation de la liaison pour créer une bibliothèque d’importation, consultez le [/DLL](../../build/reference/dll-build-a-dll.md) option.  
  
Une bibliothèque est spécifiée pour le lien comme un argument de nom de fichier ou d’une bibliothèque par défaut. LIEN résout des références externes en recherchant d’abord dans les bibliothèques spécifiées sur la ligne de commande, puis par défaut les bibliothèques spécifiées avec la [/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) option, et puis de bibliothèques par défaut nommées dans les fichiers .obj. Si un chemin d’accès est spécifié avec le nom de la bibliothèque, LINK recherche la bibliothèque dans ce répertoire. Si aucun chemin d’accès n’est spécifié, LINK recherche d’abord dans le répertoire de lien est en cours d’exécution à partir de, puis dans les répertoires spécifiés dans la variable d’environnement LIB.  
  
## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Pour ajouter des fichiers .lib en tant qu’entrée de l’éditeur de liens dans l’environnement de développement  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Choisissez le **entrée** page de propriétés dans le **l’éditeur de liens** dossier.  
  
3.  Modifier la **dépendances supplémentaires** propriété à ajouter les fichiers .lib.  
  
## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Pour ajouter par programmation les fichiers .lib en tant qu’entrée de l’éditeur de liens  
  
-   Consultez [AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx).  
  
## <a name="example"></a>Exemple  
L’exemple suivant montre comment créer et utiliser un fichier .lib. Tout d’abord, générez un fichier .lib :  
  
```cpp  
// lib_link_input_1.cpp  
// compile by using: cl /LD lib_link_input_1.cpp  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
Et ensuite, compilez cet exemple en utilisant le fichier .lib que vous venez de créer :  
  
```cpp  
// lib_link_input_2.cpp  
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp   
__declspec(dllimport) int Test();  
#include <iostream>  
int main() {  
   std::cout << Test() << std::endl;  
}  
```  
  
```Output  
213  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers d’entrée LINK](../../build/reference/link-input-files.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)
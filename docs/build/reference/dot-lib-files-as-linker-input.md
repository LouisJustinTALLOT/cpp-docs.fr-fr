---
title: .Fichiers .lib en tant qu'entrée de l'Éditeur de liens
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
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
ms.openlocfilehash: f3b2ae0d82e682cc89243b7b527ee6e0b51d4c3d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426769"
---
# <a name="lib-files-as-linker-input"></a>.Fichiers .lib en tant qu'entrée de l'Éditeur de liens

LIEN accepte les bibliothèques standard COFF et COFF bibliothèques d’importation, deux d'entre eux ont généralement l’extension. lib. Les bibliothèques standard contiennent des objets et sont créées par l’outil LIB. Bibliothèques d’importation contiennent des informations sur les exportations dans d’autres programmes et sont créées en lien lorsqu’il génère un programme qui contient des exportations ou par l’outil LIB. Pour plus d’informations sur l’utilisation de LIB pour créer standard ou des bibliothèques d’importation, consultez [Référence LIB](../../build/reference/lib-reference.md). Pour plus d’informations sur l’utilisation de lien pour créer une bibliothèque d’importation, consultez le [/DLL](../../build/reference/dll-build-a-dll.md) option.

Une bibliothèque est spécifiée pour le lien comme un argument de nom de fichier ou une bibliothèque par défaut. LIEN résout des références externes en recherchant d’abord dans les bibliothèques spécifiées sur la ligne de commande, puis par défaut spécifié de bibliothèques avec le [/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md) option, et puis en bibliothèques par défaut nommées dans les fichiers .obj. Si un chemin d’accès est spécifié avec le nom de la bibliothèque, lien recherche la bibliothèque dans ce répertoire. Si aucun chemin n’est spécifié, LINK recherche d’abord dans le répertoire de lien est en cours d’exécution à partir de, puis, dans les répertoires spécifiés dans la variable d’environnement LIB.

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Pour ajouter des fichiers .lib en tant qu’entrée de l’éditeur de liens dans l’environnement de développement

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Choisissez le **entrée** page de propriétés dans le **l’éditeur de liens** dossier.

1. Modifier le **dépendances supplémentaires** propriété à ajouter les fichiers .lib.

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Pour ajouter par programmation des fichiers .lib en tant qu’entrée de l’éditeur de liens

- Consultez [AdditionalDependencies](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies).

## <a name="example"></a>Exemple

L’exemple suivant montre comment créer et utiliser un fichier .lib. Tout d’abord, créez un fichier .lib :

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

[Fichiers d’entrée LINK](../../build/reference/link-input-files.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)

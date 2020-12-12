---
description: En savoir plus sur :. Fichiers lib en tant qu’entrée dans l’éditeur de liens
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
ms.openlocfilehash: f4a3b6c6487947772fb72135fb26f67857f0937e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201259"
---
# <a name="lib-files-as-linker-input"></a>.Fichiers .lib en tant qu'entrée de l'Éditeur de liens

Le lien accepte les bibliothèques standard COFF et les bibliothèques d’importation COFF, qui ont généralement l’extension. lib. Les bibliothèques standard contiennent des objets et sont créées par l’outil LIB. Les bibliothèques d’importation contiennent des informations sur les exportations dans d’autres programmes et sont créées soit par lien lors de la création d’un programme qui contient des exportations, soit par l’outil LIB. Pour plus d’informations sur l’utilisation de LIB pour créer des bibliothèques standard ou d’importation, consultez [référence lib](lib-reference.md). Pour plus d’informations sur l’utilisation de LINK pour créer une bibliothèque d’importation, consultez l’option [/dll](dll-build-a-dll.md) .

Une bibliothèque est spécifiée en tant qu’argument de nom de fichier ou que bibliothèque par défaut. LINK résout les références externes en commençant par les recherches dans les bibliothèques spécifiées sur la ligne de commande, puis dans les bibliothèques par défaut spécifiées avec l’option [/DEFAULTLIB](defaultlib-specify-default-library.md) , puis dans les bibliothèques par défaut nommées dans les fichiers. obj. Si un chemin d’accès est spécifié avec le nom de la bibliothèque, LINK recherche la bibliothèque dans ce répertoire. Si aucun chemin d’accès n’est spécifié, LINK regarde d’abord dans le répertoire à partir duquel le lien est en cours d’exécution, puis dans les répertoires spécifiés dans la variable d’environnement LIB.

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>Pour ajouter des fichiers. lib en tant qu’entrée dans l’éditeur de liens dans l’environnement de développement

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Choisissez la page de propriétés **entrée** dans le dossier de l' **éditeur de liens** .

1. Modifiez la propriété **dépendances supplémentaires** pour ajouter les fichiers. lib.

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>Pour ajouter par programme des fichiers. lib en tant qu’entrée dans l’éditeur de liens

- Consultez [AdditionalDependencies](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies).

## <a name="example"></a>Exemple

L’exemple suivant montre comment générer et utiliser un fichier. lib. Tout d’abord, générez un fichier. lib :

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

Puis, compilez cet exemple à l’aide du fichier. lib que vous venez de créer :

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

[Fichiers d’entrée de lien](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

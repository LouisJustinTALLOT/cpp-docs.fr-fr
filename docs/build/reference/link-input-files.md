---
title: Fichiers d'entrée LINK
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328205"
---
# <a name="link-input-files"></a>Fichiers d'entrée LINK

Vous fournissez le lien avec des fichiers qui contiennent des objets, des bibliothèques d’importation et standard, des ressources, des définitions de modules et des entrées de commande. LINK n’utilise pas les extensions de fichiers pour faire des hypothèses sur le contenu d’un fichier. Au lieu de cela, LINK examine chaque fichier d’entrée pour déterminer quel type de fichier il est.

Les fichiers d’objets sur la ligne de commande sont traités dans l’ordre qu’ils apparaissent sur la ligne de commande. Les bibliothèques sont également recherchées dans l’ordre de la ligne de commandement, avec la mise en garde suivante : Les symboles qui ne sont pas résolus lors de l’introduction d’un fichier d’objets à partir d’une bibliothèque sont recherchés dans cette bibliothèque d’abord, puis les bibliothèques suivantes de la ligne de commande et [/DEFAULTLIB (Specify Default Library)](defaultlib-specify-default-library.md) directives, puis à toutes les bibliothèques au début de la ligne de commande.

> [!NOTE]
> LINK n’accepte plus un point-virgule (ou tout autre personnage) comme le début d’un commentaire dans les fichiers de réponse et les fichiers de commande. Les semicolons ne sont reconnus que comme le début des commentaires dans les fichiers de définition de module (.def).

LINK utilise les types suivants de fichiers d’entrée :

- [fichiers .obj](dot-obj-files-as-linker-input.md)

- [.netmodule fichiers](netmodule-files-as-linker-input.md)

- [fichiers .lib](dot-lib-files-as-linker-input.md)

- [.exp fichiers](dot-exp-files-as-linker-input.md)

- [.def fichiers](dot-def-files-as-linker-input.md)

- [fichiers .pdb](dot-pdb-files-as-linker-input.md)

- [.res fichiers](dot-res-files-as-linker-input.md)

- [.exe fichiers](dot-exe-files-as-linker-input.md)

- [fichiers .txt](dot-txt-files-as-linker-input.md)

- [fichiers .ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

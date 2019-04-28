---
title: Erreur des outils Éditeur de liens LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: 657e78ece2ce4039eb8dc8561abd455c60aaff75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254912"
---
# <a name="linker-tools-error-lnk1181"></a>Erreur des outils Éditeur de liens LNK1181

Impossible d’ouvrir le fichier d’entrée 'nom_fichier'

L’éditeur de liens n’a pas pu trouver `filename` , car il n’existe pas ou le chemin d’accès est introuvable.

Certaines causes courantes pour l’erreur LNK1181 incluent :

- `filename` est référencé comme dépendance supplémentaire sur la ligne de l’éditeur de liens, mais le fichier n’existe pas.

- Un **/LIBPATH** instruction qui spécifie le répertoire contenant `filename` est manquant.

Pour résoudre les problèmes ci-dessus, vérifiez que les fichiers référencés sur la ligne de l’éditeur de liens sont présents sur le système.  Également Vérifiez qu’il existe un **/LIBPATH** instruction pour chaque répertoire contenant un fichier dépendant de l’éditeur de liens.

Pour plus d’informations, consultez [fichiers .lib en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).

Une autre cause possible pour LNK1181 est qu’un nom de fichier long avec des espaces incorporés n’était pas entre guillemets.  Dans ce cas, l’éditeur de liens reconnaîtra uniquement un nom de fichier jusqu’au premier espace et puis supposent une extension de fichier. obj.  La solution à cette situation consiste à placer le nom de fichier long (chemin d’accès plus nom de fichier) entre guillemets.

Compilation avec le [/P (Prétraiter dans un fichier)](../../build/reference/p-preprocess-to-a-file.md) option peut entraîner LNK1181, car cette option supprime la création de fichiers .obj.

## <a name="see-also"></a>Voir aussi

[/LIBPATH (Autre chemin de bibliothèque)](../../build/reference/libpath-additional-libpath.md)
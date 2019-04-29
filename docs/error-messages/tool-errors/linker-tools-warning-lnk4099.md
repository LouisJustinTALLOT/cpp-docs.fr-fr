---
title: Avertissement des outils Éditeur de liens LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: dcf4d44c3a0b5b10035af763040c2912afc8c6f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310888"
---
# <a name="linker-tools-warning-lnk4099"></a>Avertissement des outils Éditeur de liens LNK4099

Fichier PDB 'nom_fichier' est introuvable avec 'objet/bibliothèque' ou 'path' ; objet sera lié sans informations de débogage

L’éditeur de liens n’a pas pu trouver votre fichier .pdb. Copier dans le répertoire qui contient `object/library`.

Pour rechercher le nom du fichier .pdb associé au fichier objet :

1. Extrayez un fichier objet de la bibliothèque avec [lib](../../build/reference/lib-reference.md) **/extraire :**`objectname`**.obj** `xyz` **.lib**.

1. Vérifiez le chemin d’accès au fichier .pdb avec **dumpbin/section :.Debug$ T /rawdata** `objectname` **.obj**.

Vous pouvez également compiler avec [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), de sorte que le fichier pdb n’a pas besoin être utilisé, ou supprimer le [/DEBUG](../../build/reference/debug-generate-debug-info.md) option de l’éditeur de liens si vous n’avez pas les fichiers .pdb pour les objets que vous établissez une liaison.
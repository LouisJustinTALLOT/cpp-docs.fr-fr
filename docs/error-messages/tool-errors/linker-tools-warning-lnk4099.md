---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4099'
title: Avertissement des outils Éditeur de liens LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: 1e063cce9c884b8952e4bd5807b0d4a7683d4d54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133768"
---
# <a name="linker-tools-warning-lnk4099"></a>Avertissement des outils Éditeur de liens LNK4099

Le fichier PDB’filename’est introuvable avec’Object/Library’ou’Path'; liaison de l’objet comme si aucune information de débogage

L’éditeur de liens n’a pas pu trouver votre fichier. pdb. Copiez-le dans le répertoire qui contient `object/library` .

Pour rechercher le nom du fichier. pdb associé au fichier objet :

1. Extrayez un fichier objet de la bibliothèque avec [lib](../../build/reference/lib-reference.md) **/extract :** `objectname` **. obj** `xyz` **. lib**.

1. Vérifiez le chemin d’accès au fichier. pdb avec l' **/section de DUMPBIN :. Debug $ T/rawData** `objectname` **. obj**.

Vous pouvez également compiler avec [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), de sorte que le fichier PDB n’a pas besoin d’être utilisé, ou supprimer l’option [/Debug](../../build/reference/debug-generate-debug-info.md) de l’éditeur de liens si vous n’avez pas de fichiers. pdb pour les objets que vous liez.

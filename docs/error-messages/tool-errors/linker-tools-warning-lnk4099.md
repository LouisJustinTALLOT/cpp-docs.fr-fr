---
title: LNK4099 d’avertissement des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50bdceaba2e72312febec4819b96df334b5398c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025999"
---
# <a name="linker-tools-warning-lnk4099"></a>Avertissement des outils Éditeur de liens LNK4099

Fichier PDB 'nom_fichier' est introuvable avec 'objet/bibliothèque' ou 'path' ; objet sera lié sans informations de débogage

L’éditeur de liens n’a pas pu trouver votre fichier .pdb. Copier dans le répertoire qui contient `object/library`.

Pour rechercher le nom du fichier .pdb associé au fichier objet :

1. Extrayez un fichier objet de la bibliothèque avec [lib](../../build/reference/lib-reference.md) **/extraire :**`objectname`**.obj** `xyz` **.lib**.

1. Vérifiez le chemin d’accès au fichier .pdb avec **dumpbin/section :.Debug$ T /rawdata** `objectname` **.obj**.

Vous pouvez également compiler avec [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), de sorte que le fichier pdb n’a pas besoin être utilisé, ou supprimer le [/DEBUG](../../build/reference/debug-generate-debug-info.md) option de l’éditeur de liens si vous n’avez pas les fichiers .pdb pour les objets que vous établissez une liaison.
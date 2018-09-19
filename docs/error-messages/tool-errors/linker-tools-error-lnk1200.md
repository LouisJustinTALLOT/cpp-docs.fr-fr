---
title: LNK1200 d’erreur des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03ecd51142bf30230b6b177a36e007345e93bf2c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059314"
---
# <a name="linker-tools-error-lnk1200"></a>Erreur des outils Éditeur de liens LNK1200

Erreur de lecture de base de données du programme 'nom_fichier'

La base de données du programme (PDB) n’a pas pu être lu.

Cette erreur peut être dû à l’endommagement du fichier.

Si `filename` est le fichier PDB d’un fichier objet, recompilez le fichier objet en utilisant [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` est le fichier PDB pour le fichier de sortie principal, et cette erreur s’est produite au cours d’une édition de liens incrémentielle, supprimez le PDB et rétablir.
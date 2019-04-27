---
title: Erreur des outils Éditeur de liens LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213548"
---
# <a name="linker-tools-error-lnk1200"></a>Erreur des outils Éditeur de liens LNK1200

Erreur de lecture de base de données du programme 'nom_fichier'

La base de données du programme (PDB) n’a pas pu être lu.

Cette erreur peut être dû à l’endommagement du fichier.

Si `filename` est le fichier PDB d’un fichier objet, recompilez le fichier objet en utilisant [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` est le fichier PDB pour le fichier de sortie principal, et cette erreur s’est produite au cours d’une édition de liens incrémentielle, supprimez le PDB et rétablir.
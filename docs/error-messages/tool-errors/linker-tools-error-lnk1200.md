---
title: Erreur des outils Éditeur de liens LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195134"
---
# <a name="linker-tools-error-lnk1200"></a>Erreur des outils Éditeur de liens LNK1200

erreur lors de la lecture de la base de données du programme’nom_fichier'

Impossible de lire la base de données du programme (PDB).

Cette erreur peut être due à l’endommagement d’un fichier.

Si `filename` est le PDB d’un fichier objet, recompilez le fichier objet à l’aide de [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` est le PDB du fichier de sortie principal et que cette erreur s’est produite lors d’un lien incrémentiel, supprimez le PDB et reliez-le.

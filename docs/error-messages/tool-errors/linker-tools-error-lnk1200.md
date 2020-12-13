---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1200'
title: Erreur des outils Éditeur de liens LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: b8c380b16cef47a4b340e4a48853d58d1ab203e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341644"
---
# <a name="linker-tools-error-lnk1200"></a>Erreur des outils Éditeur de liens LNK1200

erreur lors de la lecture de la base de données du programme’nom_fichier'

Impossible de lire la base de données du programme (PDB).

Cette erreur peut être due à l’endommagement d’un fichier.

Si `filename` est le PDB d’un fichier objet, recompilez le fichier objet à l’aide de [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` est le PDB du fichier de sortie principal et que cette erreur s’est produite lors d’un lien incrémentiel, supprimez le PDB et reliez-le.

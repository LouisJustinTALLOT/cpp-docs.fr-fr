---
title: Priorité dans les définitions de macros
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 38a653a9f460beae81f9f88ea457870d30f25339
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320160"
---
# <a name="precedence-in-macro-definitions"></a>Priorité dans les définitions de macros

Si une macro a plusieurs définitions, NMAKE utilise la définition de la priorité la plus élevée. La liste suivante montre l’ordre de priorité, du plus élevé au plus bas :

1. Une macro définie sur la ligne de commande

1. Une macro définie dans un makefile ou fichier include

1. Une macro héritée de la variable d’environnement

1. Une macro définie dans le fichier Tools.ini

1. Une macro prédéfinie, tel que [CC](command-macros-and-options-macros.md) et [AS](command-macros-and-options-macros.md)

Utilisez /E pour que les macros héritées de variables d’environnement substituent les macros du makefile portant le même nom. Utilisez **! UNDEF** pour remplacer une ligne de commande.

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](defining-an-nmake-macro.md)

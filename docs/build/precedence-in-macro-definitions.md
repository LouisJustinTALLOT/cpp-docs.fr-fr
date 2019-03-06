---
title: Priorité dans les définitions de macros
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 7f847cd7cea736ff9b4360a050767d00bd6cf539
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421500"
---
# <a name="precedence-in-macro-definitions"></a>Priorité dans les définitions de macros

Si une macro a plusieurs définitions, NMAKE utilise la définition de la priorité la plus élevée. La liste suivante montre l’ordre de priorité, du plus élevé au plus bas :

1. Une macro définie sur la ligne de commande

1. Une macro définie dans un makefile ou fichier include

1. Une macro héritée de la variable d’environnement

1. Une macro définie dans le fichier Tools.ini

1. Une macro prédéfinie, tel que [CC](../build/command-macros-and-options-macros.md) et [AS](../build/command-macros-and-options-macros.md)

Utilisez /E pour que les macros héritées de variables d’environnement substituent les macros du makefile portant le même nom. Utilisez **! UNDEF** pour remplacer une ligne de commande.

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](../build/defining-an-nmake-macro.md)

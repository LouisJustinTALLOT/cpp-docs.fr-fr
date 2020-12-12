---
description: 'En savoir plus sur : précédence dans les définitions de macros'
title: Priorité dans les définitions de macros
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
ms.openlocfilehash: 1738c4ba77f330103395278a6daae169b04fae4c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225893"
---
# <a name="precedence-in-macro-definitions"></a>Priorité dans les définitions de macros

Si une macro a plusieurs définitions, NMAKE utilise la définition de priorité la plus élevée. La liste suivante indique l’ordre de priorité, du plus élevé au plus bas :

1. Macro définie sur la ligne de commande

1. Macro définie dans un fichier Make ou include

1. Une macro de variable d’environnement héritée

1. Macro définie dans le fichier Tools.ini

1. Macro prédéfinie, telle que [CC](command-macros-and-options-macros.md) et [As](command-macros-and-options-macros.md)

Utilisez/E pour que les macros héritées des variables d’environnement remplacent les macros Makefile portant le même nom. Utilisez **! UNDEF** pour remplacer une ligne de commande.

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](defining-an-nmake-macro.md)

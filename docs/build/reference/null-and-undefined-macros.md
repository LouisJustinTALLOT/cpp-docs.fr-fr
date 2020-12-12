---
description: En savoir plus sur les macros null et non définies
title: Macros nulles et non définies
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
ms.openlocfilehash: 639afda727f1ebb1f4d7d602ed7cf01d6c914a33
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209722"
---
# <a name="null-and-undefined-macros"></a>Macros nulles et non définies

Les macros null et non définies se développent en chaînes NULL, mais une macro définie en tant que chaîne NULL est considérée comme définie dans les expressions de prétraitement. Pour définir une macro comme une chaîne NULL, ne spécifiez aucun caractère à l’exception des espaces ou des tabulations après le signe égal (=) dans une ligne de commande ou un fichier de commandes, et placez la chaîne ou la définition null entre guillemets doubles (""). Pour annuler la définition d’une macro, utilisez **! UNDEF.** Pour plus d’informations, consultez [directives de prétraitement](makefile-preprocessing-directives.md)d’un Makefile.

## <a name="see-also"></a>Voir aussi

[Définition d’une macro NMAKE](defining-an-nmake-macro.md)

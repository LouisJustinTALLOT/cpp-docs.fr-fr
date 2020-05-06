---
title: Dépassement des valeurs à virgule flottante
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344061"
---
# <a name="underflow-of-floating-point-values"></a>Dépassement des valeurs à virgule flottante

**ANSI 4.5.1** Indique si les fonctions mathématiques définissent l'expression d'entier `errno` sur la valeur de la macro `ERANGE` sur les erreurs de plage de dépassement de capacité négatif

Un dépassement de capacité négatif à virgule flottante ne définit pas l'expression `errno` sur `ERANGE`. Lorsqu'une valeur s'approche de zéro et effectue finalement un dépassement de capacité négatif, la valeur est définie sur zéro.

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)

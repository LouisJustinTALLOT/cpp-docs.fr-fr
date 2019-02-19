---
title: Dépassement des valeurs à virgule flottante
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149924"
---
# <a name="underflow-of-floating-point-values"></a>Dépassement des valeurs à virgule flottante

**ANSI 4.5.1** Indique si les fonctions mathématiques définissent l'expression d'entier `errno` sur la valeur de la macro `ERANGE` sur les erreurs de plage de dépassement de capacité négatif

Un dépassement de capacité négatif à virgule flottante ne définit pas l'expression `errno` sur `ERANGE`. Lorsqu'une valeur s'approche de zéro et effectue finalement un dépassement de capacité négatif, la valeur est définie sur zéro.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)

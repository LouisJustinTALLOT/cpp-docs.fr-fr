---
description: 'En savoir plus sur : dépassement de capacité négatif des valeurs de Floating-Point'
title: Dépassement des valeurs à virgule flottante
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 3d8ddd665aa33e1c47f9f187f759058501bc5484
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321295"
---
# <a name="underflow-of-floating-point-values"></a>Dépassement des valeurs à virgule flottante

**ANSI 4.5.1** Indique si les fonctions mathématiques définissent l'expression d'entier `errno` sur la valeur de la macro `ERANGE` sur les erreurs de plage de dépassement de capacité négatif

Un dépassement de capacité négatif à virgule flottante ne définit pas l'expression `errno` sur `ERANGE`. Lorsqu'une valeur s'approche de zéro et effectue finalement un dépassement de capacité négatif, la valeur est définie sur zéro.

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)

---
title: Erreur mathématique M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 6d3f107de7e45653374036ecafaa864cb3eff5b0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622103"
---
# <a name="math-error-m6201"></a>Erreur mathématique M6201

'fonction' : erreur de _domaine

Un argument de la fonction était en dehors du domaine des valeurs d’entrée autorisées pour cette fonction.

## <a name="example"></a>Exemple

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Cette erreur appelle le `_matherr` fonction avec le nom de fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction permettant de personnaliser la gestion de certaines erreurs mathématiques à virgule flottante d’exécution.
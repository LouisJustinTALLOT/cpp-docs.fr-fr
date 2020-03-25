---
title: Erreur mathématique M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193704"
---
# <a name="math-error-m6201"></a>Erreur mathématique M6201

'fonction' : erreur _DOMAIN

Un argument de la fonction donnée se trouvait en dehors du domaine des valeurs d’entrée autorisées pour cette fonction.

## <a name="example"></a>Exemple

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Cette erreur appelle la fonction `_matherr` avec le nom de la fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la fonction `_matherr` pour personnaliser la gestion de certaines erreurs mathématiques à virgule flottante au moment de l’exécution.

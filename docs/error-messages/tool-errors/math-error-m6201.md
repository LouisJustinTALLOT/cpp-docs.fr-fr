---
description: 'En savoir plus sur : erreur mathématique mathématique M6201'
title: Erreur mathématique M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 03588b7eed580b95cb263f6e4d71f5a793f4d392
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244314"
---
# <a name="math-error-m6201"></a>Erreur mathématique M6201

'fonction' : erreur _DOMAIN

Un argument de la fonction donnée se trouvait en dehors du domaine des valeurs d’entrée autorisées pour cette fonction.

## <a name="example"></a>Exemple

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Cette erreur appelle la `_matherr` fonction avec le nom de la fonction, ses arguments et le type d’erreur. Vous pouvez réécrire la `_matherr` fonction pour personnaliser la gestion de certaines erreurs mathématiques à virgule flottante au moment de l’exécution.

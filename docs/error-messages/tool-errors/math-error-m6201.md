---
title: Erreur mathématique M6201 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d2c09d6448bcf7fb0557fa3a174c60205a34ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099393"
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
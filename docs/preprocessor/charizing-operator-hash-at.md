---
title: Opérateur charizing (#@)
ms.date: 11/04/2016
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: c9acc9b9872e096cd441b950632c341e975fecb8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034333"
---
# <a name="charizing-operator-"></a>Opérateur charizing (#@)
**Section spécifique à Microsoft**

L’opérateur charizing peut être utilisé uniquement avec des arguments de macros. Si `#@` précède un paramètre formel dans la définition de la macro, l’argument réel est placé entre guillemets simples et traité comme un caractère lorsque la macro est développée. Exemple :

```
#define makechar(x)  #@x
```

provoque le développement de l'instruction

```
a = makechar(b);
```

à développer en

```
a = 'b';
```

Le guillemet simple ne peut pas être utilisé avec l'opérateur charizing.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)
---
title: Opérateur charizing (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218535"
---
# <a name="charizing-operator-"></a>Opérateur charizing (#@)

**Section spécifique à Microsoft**

L’opérateur charizing peut être utilisé uniquement avec des arguments de macros. Si `#@` précède un paramètre formel dans la définition de la macro, l’argument réel est placé entre guillemets simples et traité comme un caractère lorsque la macro est développée. Par exemple :

```cpp
#define makechar(x)  #@x
```

provoque le développement de l'instruction

```cpp
a = makechar(b);
```

à développer en

```cpp
a = 'b';
```

Le caractère de citation simple (`'`) ne peut pas être utilisé avec l’opérateur de caractères.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)

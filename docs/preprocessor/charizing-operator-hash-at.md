---
description: 'En savoir plus sur : opérateur de caractères (# @)'
title: Opérateur charizing (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: 6d04aa24c75153957bd6fd09824f4e94e36fd38f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300864"
---
# <a name="charizing-operator-"></a>Opérateur charizing (#@)

**Spécifique à Microsoft**

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

Le caractère de citation simple ( `'` ) ne peut pas être utilisé avec l’opérateur de caractères.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)

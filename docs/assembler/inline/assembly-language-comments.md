---
title: Commentaires relatifs au langage assembleur
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: 2e993bd48c7ec801abd440676c80a5bd8f7b42ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192728"
---
# <a name="assembly-language-comments"></a>Commentaires relatifs au langage assembleur

**Spécifique à Microsoft**

Les instructions contenues dans un **`__asm`** bloc peuvent utiliser des commentaires en langage assembleur :

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Comme les macros C sont développées en une ligne logique unique, évitez d’utiliser des commentaires en langage assembleur dans les macros. (Consultez [définition de blocs __asm en tant que macros C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Un **`__asm`** bloc peut également contenir des commentaires de style C ; pour plus d’informations, consultez [utilisation de c ou C++ dans des blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>

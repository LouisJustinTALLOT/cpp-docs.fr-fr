---
title: Commentaires relatifs au langage assembleur
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: fc37658eccd99b61d45aa9a9a7a2675ef90eee89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578637"
---
# <a name="assembly-language-comments"></a>Commentaires relatifs au langage assembleur

**Section spécifique à Microsoft**

Les instructions figurant dans un bloc `__asm` peuvent utiliser des commentaires en langage assembleur :

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Comme les macros C sont développées en une ligne logique unique, évitez d’utiliser des commentaires en langage assembleur dans les macros. (Consultez [définition des blocs __asm en tant que Macros C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Un `__asm` bloc peut également contenir des commentaires de style C ; pour plus d’informations, consultez [à l’aide de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
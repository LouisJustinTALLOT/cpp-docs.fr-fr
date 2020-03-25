---
title: Commentaires relatifs au langage assembleur
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: a8b2c98c61d58d72e78dbffd4f3b6ed7707d2d7a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169602"
---
# <a name="assembly-language-comments"></a>Commentaires relatifs au langage assembleur

**Section spécifique de Microsoft**

Les instructions figurant dans un bloc `__asm` peuvent utiliser des commentaires en langage assembleur :

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Comme les macros C sont développées en une ligne logique unique, évitez d’utiliser des commentaires en langage assembleur dans les macros. (Consultez [définition de blocs __asm en tant que macros C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Un bloc `__asm` peut également contenir des commentaires de style C ; Pour plus d’informations, consultez [utilisation de C++ C ou de blocs de __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>

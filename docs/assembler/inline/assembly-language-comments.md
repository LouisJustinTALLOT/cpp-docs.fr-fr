---
description: 'En savoir plus sur : commentaires Assembly-Language'
title: Commentaires relatifs au langage assembleur
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: 704f5275afe5cb5629b2e7667fe9107417512198
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118002"
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

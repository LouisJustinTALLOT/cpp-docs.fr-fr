---
title: Commentaires en langage assembleur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 048635a874db604f872b4fa87d72bd06d0455438
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050761"
---
# <a name="assembly-language-comments"></a>Commentaires relatifs au langage assembleur
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Les instructions figurant dans un bloc `__asm` peuvent utiliser des commentaires en langage assembleur :  
  
```  
__asm mov ax, offset buff ; Load address of buff  
```  
  
 Comme les macros C sont développées en une ligne logique unique, évitez d’utiliser des commentaires en langage assembleur dans les macros. (Consultez [définition des blocs __asm en tant que Macros C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) Un `__asm` bloc peut également contenir des commentaires de style C ; pour plus d’informations, consultez [à l’aide de C ou C++ dans les blocs __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)
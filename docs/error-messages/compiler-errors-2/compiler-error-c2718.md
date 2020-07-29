---
title: Erreur du compilateur C2718
ms.date: 11/04/2016
f1_keywords:
- C2718
helpviewer_keywords:
- C2718
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
ms.openlocfilehash: 8088fd62baeffb7d53a1be2b5bccae72913cdc12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216061"
---
# <a name="compiler-error-c2718"></a>Erreur du compilateur C2718

'paramètre' : le paramètre réel avec __declspec (align (' # ')) ne sera pas aligné

Le [align](../../cpp/align-cpp.md) **`__declspec`** modificateur align n’est pas autorisé sur les paramètres de fonction.

L’exemple suivant génère l’C2718 :

```cpp
// C2718.cpp
typedef struct __declspec(align(32)) AlignedStruct  {
   int i;
} AlignedStruct;

void f2(int i, ...);

void f4() {
   AlignedStruct as;

   f2(0, as);   // C2718, actual parameter is aligned
}
```

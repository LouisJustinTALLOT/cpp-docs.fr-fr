---
description: 'En savoir plus sur : erreur du compilateur C2718'
title: Erreur du compilateur C2718
ms.date: 11/04/2016
f1_keywords:
- C2718
helpviewer_keywords:
- C2718
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
ms.openlocfilehash: ab0ddd8f5afa8cc72259f527d0bb8731fa4e9a5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320783"
---
# <a name="compiler-error-c2718"></a>Erreur du compilateur C2718

'paramètre' : le paramètre réel avec __declspec (align (' # ')) ne sera pas aligné

Le [](../../cpp/align-cpp.md) **`__declspec`** modificateur align n’est pas autorisé sur les paramètres de fonction.

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

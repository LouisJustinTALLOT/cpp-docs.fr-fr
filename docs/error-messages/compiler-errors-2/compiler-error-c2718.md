---
title: Erreur du compilateur C2718 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2718
dev_langs:
- C++
helpviewer_keywords:
- C2718
ms.assetid: 78cc71f8-c142-46fc-9aed-970635d74f0c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: facbee46968cf76e6709bceff4432ba289aed3cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045768"
---
# <a name="compiler-error-c2718"></a>Erreur du compilateur C2718

'paramètre' : le paramètre réel avec __declspec(align('#')) ne sera pas aligné

Le [aligner](../../cpp/align-cpp.md) `__declspec` modificateur n’est pas autorisé sur les paramètres de fonction.

L’exemple suivant génère l’erreur C2718 :

```
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
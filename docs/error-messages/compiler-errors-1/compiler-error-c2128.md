---
title: Erreur du compilateur C2128 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c2128
dev_langs:
- C++
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecd2b7eb2db0828387bd2c933b51ee39c00bae77
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066711"
---
# <a name="compiler-error-c2128"></a>Erreur du compilateur C2128

'fonction' : alloc_text/same_seg applicable uniquement aux fonctions avec liaison C

`pragma` `alloc_text` peut uniquement être utilisé avec les fonctions déclarées liaison C.

L’exemple suivant génère C2128 :

```
// C2128.cpp
// compile with: /c

// Delete the following line to resolve.
void func();
// #pragma alloc_text("my segment", func)   // C2128

extern "C" {
void func();
}

#pragma alloc_text("my segment", func)
void func() {}
```
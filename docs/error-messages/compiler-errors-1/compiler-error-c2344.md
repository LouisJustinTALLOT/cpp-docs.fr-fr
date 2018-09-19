---
title: Erreur du compilateur C2344 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2344
dev_langs:
- C++
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c560d1fcd250a83501579ec80768b4ba2de57f0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110213"
---
# <a name="compiler-error-c2344"></a>Erreur du compilateur C2344

align(#) : l’alignement doit être une puissance de deux

Quand vous utilisez le mot clé [align](../../cpp/align-cpp.md) , la valeur que vous passez doit être une puissance de deux.

Par exemple, le code suivant génère l’erreur C2344, car 3 n’est pas une puissance de deux :

```
// C2344.cpp
// compile with: /c
__declspec(align(3)) int a;   // C2344
__declspec(align(4)) int b;   // OK
```
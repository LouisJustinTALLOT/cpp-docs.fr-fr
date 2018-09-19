---
title: Compilateur avertissement (niveau 3) C4290 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a6f09d8f3396381f34a0fbe3c7150b5948cee01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015966"
---
# <a name="compiler-warning-level-3-c4290"></a>Avertissement du compilateur (niveau 3) C4290

Spécification d’exception C++ ignorée sauf to indiquer qu’une fonction n’est pas __declspec (nothrow)

Une fonction est déclarée à l’aide de la spécification d’exception, qui accepte de Visual C++, mais n’implémente pas. Code avec l’exception des spécifications sont ignorées pendant la compilation peuvent doivent être recompilés et lié à être réutilisé dans les futures versions prenant en charge les spécifications d’exceptions.

Pour plus d’informations, consultez [spécifications d’Exception (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Vous pouvez éviter cet avertissement en utilisant la [avertissement](../../preprocessor/warning.md) pragma :

```
#pragma warning( disable : 4290 )
```

L’exemple de code suivant génère C4290 :

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```
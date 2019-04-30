---
title: Avertissement du compilateur (niveau 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: c585294686298a1197d437d41a0d541f1268985f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402084"
---
# <a name="compiler-warning-level-3-c4290"></a>Avertissement du compilateur (niveau 3) C4290

C++spécification d’exception ignorée excepté to indiquer qu’une fonction n’est pas __declspec (nothrow)

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
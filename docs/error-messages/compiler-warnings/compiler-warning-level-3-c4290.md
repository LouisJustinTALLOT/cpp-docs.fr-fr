---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4290'
title: Avertissement du compilateur (niveau 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 771eb01c23778a716aee22ca747ea6473909a8bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344066"
---
# <a name="compiler-warning-level-3-c4290"></a>Avertissement du compilateur (niveau 3) C4290

Spécification d’exception C++ ignorée sauf pour indiquer qu’une fonction n’est pas __declspec (nothrow)

Une fonction est déclarée à l’aide de la spécification d’exception, qui Visual C++ accepte mais n’implémente pas. Le code avec des spécifications d’exception qui sont ignorées pendant la compilation devra peut-être être recompilé et lié pour pouvoir être réutilisé dans les versions ultérieures prenant en charge les spécifications d’exception.

Pour plus d’informations, consultez [spécifications d’exception (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Vous pouvez éviter cet avertissement à l’aide du pragma [Warning](../../preprocessor/warning.md) :

```cpp
#pragma warning( disable : 4290 )
```

L’exemple de code suivant génère l’erreur C4290 :

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```

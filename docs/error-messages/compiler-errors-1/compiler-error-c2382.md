---
description: 'En savoir plus sur : erreur du compilateur C2382'
title: Erreur du compilateur C2382
ms.date: 11/04/2016
f1_keywords:
- C2382
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
ms.openlocfilehash: 31996423a059f3ec337d6ab8992360bb50508602
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185945"
---
# <a name="compiler-error-c2382"></a>Erreur du compilateur C2382

'fonction' : redéfinition ; spécifications des exceptions différentes

Sous [/Za](../../build/reference/za-ze-disable-language-extensions.md), cette erreur indique qu’une surcharge de fonction n’a été tentée que sur la [spécification d’exception](../../cpp/exception-specifications-throw-cpp.md).

L’exemple suivant génère l’erreur C2382 :

```cpp
// C2382.cpp
// compile with: /Za /c
void f1(void) throw(int) {}
void f1(void) throw(char) {}   // C2382
void f2(void) throw(char) {}   // OK
```

---
description: 'En savoir plus sur : erreur du compilateur C2498'
title: Erreur du compilateur C2498
ms.date: 11/04/2016
f1_keywords:
- C2498
helpviewer_keywords:
- C2498
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
ms.openlocfilehash: e7cbb811cdaeea703d0f1da1c0f2012ebe8210fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335098"
---
# <a name="compiler-error-c2498"></a>Erreur du compilateur C2498

'fonction' : 'novtable’ne peut s’appliquer qu’aux définitions ou déclarations de classe

Cette erreur peut être due à l’utilisation de `__declspec(novtable)` avec une fonction.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2498 :

```cpp
// C2498.cpp
// compile with: /c
void __declspec(novtable) f() {}   // C2498
class __declspec(novtable) A {};   // OK
```

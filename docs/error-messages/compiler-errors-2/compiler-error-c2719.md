---
title: Erreur du compilateur C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: 574a04923c20c3104083a6aa05a71838e7ec13d2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760502"
---
# <a name="compiler-error-c2719"></a>Erreur du compilateur C2719

'paramètre' : le paramètre formel avec __declspec(align('#')) ne sera pas aligné

Le modificateur [align](../../cpp/align-cpp.md) `__declspec` n’est pas autorisé sur les paramètres de fonction. L’alignement des paramètres de fonction est contrôlé par la convention d’appel utilisée. Pour plus d’informations, consultez [conventions d’appel](../../cpp/calling-conventions.md).

L'exemple suivant génère l'erreur C2719 et montre comment la corriger :

```cpp
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```

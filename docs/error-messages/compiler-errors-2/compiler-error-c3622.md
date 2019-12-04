---
title: Erreur du compilateur C3622
ms.date: 11/04/2016
f1_keywords:
- C3622
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
ms.openlocfilehash: 2adcee4cb20c39c39b06e0ac2087478cfe2d8937
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740895"
---
# <a name="compiler-error-c3622"></a>Erreur du compilateur C3622

'classe' : une classe déclarée comme’keyword’ne peut pas être instanciée

Une tentative a été effectuée pour instancier une classe marquée comme [abstract](../../extensions/abstract-cpp-component-extensions.md). Une classe marquée comme `abstract` peut être une classe de base, mais elle ne peut pas être instanciée.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3622.

```cpp
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```

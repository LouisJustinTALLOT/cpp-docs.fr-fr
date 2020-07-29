---
title: Avertissement du compilateur (niveau 4) C4670
ms.date: 11/04/2016
f1_keywords:
- C4670
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
ms.openlocfilehash: 15f0b249d9e91c0ebcc5655b5edffbd2d8cafa93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230608"
---
# <a name="compiler-warning-level-4-c4670"></a>Avertissement du compilateur (niveau 4) C4670

'identificateur' : cette classe de base n’est pas accessible

La classe de base spécifiée d’un objet à lever dans un **`try`** bloc n’est pas accessible. L’objet ne peut pas être instancié s’il est levé. Vérifiez que la classe de base est héritée avec le bon spécificateur d’accès.

L’exemple suivant génère l’avertissement C4670 :

```cpp
// C4670.cpp
// compile with: /EHsc /W4
class A
{
};

class B : /* public */ A
{
} b;   // inherits A with private access by default

int main()
{
    try
    {
       throw b;   // C4670
    }
    catch( B )
    {
    }
}
```

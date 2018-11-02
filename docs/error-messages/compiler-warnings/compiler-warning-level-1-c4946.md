---
title: Avertissement du compilateur (niveau 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: f215c621486bf223d8f6c90b0a4f4ae119ad4b1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574224"
---
# <a name="compiler-warning-level-1-c4946"></a>Avertissement du compilateur (niveau 1) C4946

reinterpret_cast utilisé entre des classes connexes : 'classe1' et 'classe2'

N’utilisez pas [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) pour effectuer un cast entre types connexes. Utilisez [static_cast](../../cpp/static-cast-operator.md) à la place des types polymorphes, utilisez [dynamic_cast](../../cpp/dynamic-cast-operator.md).

Par défaut, cet avertissement est désactivé. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

L’exemple de code suivant génère l’erreur C4946 :

```
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```
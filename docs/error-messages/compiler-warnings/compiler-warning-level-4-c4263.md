---
title: Avertissement du compilateur (niveau 4) C4263
ms.date: 11/04/2016
f1_keywords:
- C4263
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
ms.openlocfilehash: ea41f16420f847616b5bcb2c092ff187a14f7175
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541660"
---
# <a name="compiler-warning-level-4-c4263"></a>Avertissement du compilateur (niveau 4) C4263

'fonction' : la fonction membre ne se substitue à aucune fonction membre virtuelle de classe de base

Une définition de fonction de classe a le même nom qu’une fonction virtuelle dans une classe de base, mais pas le même nombre ou type d’arguments. Cela masque effectivement la fonction virtuelle dans la classe de base.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4263 :

```cpp
// C4263.cpp
// compile with: /W4
#pragma warning(default:4263)
#pragma warning(default:4264)
class B {
public:
   virtual void func();
};

class D : public B {
   void func(int);   // C4263
};

int main() {
}
```
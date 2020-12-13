---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4263'
title: Avertissement du compilateur (niveau 4) C4263
ms.date: 11/04/2016
f1_keywords:
- C4263
helpviewer_keywords:
- C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
ms.openlocfilehash: 7b7eb7fdf8e66ab5d09c8dc0f9511d3c88162084
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339145"
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

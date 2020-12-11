---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4373'
title: Avertissement du compilateur (niveau 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: a0688f8ed0af1c2854a4449a2fcba31d412a9e4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160452"
---
# <a name="compiler-warning-level-3-c4373"></a>Avertissement du compilateur (niveau 3) C4373

> '*fonction*' : la fonction virtuelle se substitue à'*base_function*', les versions précédentes du compilateur n’ont pas été substituées lorsque les paramètres ne différaient que par les qualificateurs const/volatile

## <a name="remarks"></a>Notes

Votre application contient une méthode dans une classe dérivée qui remplace une méthode virtuelle dans une classe de base, et les paramètres de la méthode de substitution ne diffèrent des paramètres de la méthode virtuelle que par un qualificateur [const](../../cpp/const-cpp.md) ou [volatile](../../cpp/volatile-cpp.md) . Cela signifie que le compilateur doit lier une référence de fonction à la méthode dans la classe de base ou dans la classe dérivée.

Les versions du compilateur antérieures à Visual Studio 2008 lient la fonction à la méthode dans la classe de base, puis émettent un message d’avertissement. Les versions suivantes du compilateur ignorent **`const`** le **`volatile`** qualificateur ou, lient la fonction à la méthode dans la classe dérivée, puis émettent l’avertissement **C4373**. Ce dernier comportement est conforme à la norme C++.

## <a name="example"></a>Exemple

L’exemple de code suivant génère l’avertissement C4373. Pour résoudre ce problème, vous pouvez faire en sorte que le remplacement utilise les mêmes qualificateurs CV que la fonction membre de base, ou si vous n’avez pas l’intention de créer un remplacement, vous pouvez donner un nom différent à la fonction dans la classe dérivée.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```

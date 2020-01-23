---
title: Avertissement du compilateur (niveau 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518346"
---
# <a name="compiler-warning-level-3-c4373"></a>Avertissement du compilateur (niveau 3) C4373

> '*fonction*' : la fonction virtuelle se substitue à'*base_function*', les versions précédentes du compilateur n’ont pas été substituées lorsque les paramètres ne différaient que par les qualificateurs const/volatile

## <a name="remarks"></a>Notes

Votre application contient une méthode dans une classe dérivée qui remplace une méthode virtuelle dans une classe de base, et les paramètres de la méthode de substitution ne diffèrent des paramètres de la méthode virtuelle que par un qualificateur [const](../../cpp/const-cpp.md) ou [volatile](../../cpp/volatile-cpp.md) . Cela signifie que le compilateur doit lier une référence de fonction à la méthode dans la classe de base ou dans la classe dérivée.

Les versions du compilateur antérieures à Visual Studio 2008 lient la fonction à la méthode dans la classe de base, puis émettent un message d’avertissement. Les versions suivantes du compilateur ignorent le qualificateur `const` ou `volatile`, lient la fonction à la méthode dans la classe dérivée, puis émettent l’avertissement **C4373**. Ce dernier comportement est conforme à la norme C++.

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

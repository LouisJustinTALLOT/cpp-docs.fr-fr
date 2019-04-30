---
title: Avertissement du compilateur (niveau 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 031b32a03d93a51f6fa00041a5b0bdf99e6eacf1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401993"
---
# <a name="compiler-warning-level-3-c4373"></a>Avertissement du compilateur (niveau 3) C4373

> «*fonction*' : substitutions de fonctions virtuelles*fonction_base*», les versions précédentes du compilateur n’ont pas été substituées lorsque les paramètres ne différaient que par les qualificateurs const/volatile

## <a name="remarks"></a>Notes

Votre application contient une méthode dans une classe dérivée qui remplace une méthode virtuelle dans une classe de base, et les paramètres de la méthode de substitution ne diffèrent des paramètres de la méthode virtuelle que par un qualificateur [const](../../cpp/const-cpp.md) ou [volatile](../../cpp/volatile-cpp.md) . Cela signifie que le compilateur doit lier une référence de fonction à la méthode dans la classe de base ou dans la classe dérivée.

Les versions du compilateur avant Visual Studio 2008 lient la fonction à la méthode dans la classe de base, puis émettre un message d’avertissement. Les versions suivantes du compilateur ignorent le `const` ou `volatile` qualificateur, lient la fonction à la méthode dans la classe dérivée, puis émettent l’avertissement **C4373**. Ce dernier comportement est conforme à la norme C++.

## <a name="example"></a>Exemple

L’exemple de code suivant génère l’avertissement C4373. Pour résoudre ce problème, vous pouvez soit spécifier le remplacement d’utiliser les qualificateurs CV de mêmes que la fonction membre de base, ou si vous ne souhaitez pas créer un remplacement, vous pouvez donner à la fonction dans la classe dérivée un nom différent.

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

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
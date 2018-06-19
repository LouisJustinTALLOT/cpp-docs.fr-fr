---
title: Compilateur avertissement (niveau 3) C4373 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4373
dev_langs:
- C++
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fda965fe80fc26731cde7be5a71540e6454a7360
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290177"
---
# <a name="compiler-warning-level-3-c4373"></a>Avertissement du compilateur (niveau 3) C4373

> '*fonction*' : substitutions de fonctions virtuelles*fonction_base*», les versions précédentes du compilateur n’ont pas été substituées lorsque les paramètres ne différaient que par les qualificateurs const/volatile

## <a name="remarks"></a>Notes

Votre application contient une méthode dans une classe dérivée qui remplace une méthode virtuelle dans une classe de base, et les paramètres de la méthode de substitution ne diffèrent des paramètres de la méthode virtuelle que par un qualificateur [const](../../cpp/const-cpp.md) ou [volatile](../../cpp/volatile-cpp.md) . Cela signifie que le compilateur doit lier une référence de fonction à la méthode dans la classe de base ou dans la classe dérivée.

Versions du compilateur avant Visual Studio 2008 lient la fonction à la méthode dans la classe de base, puis émet un message d’avertissement. Les versions ultérieures du compilateur ignorent le `const` ou `volatile` qualificateur, liaison de la fonction à la méthode dans la classe dérivée, puis émettent l’avertissement **C4373**. Ce dernier comportement est conforme à la norme C++.

## <a name="example"></a>Exemple

L’exemple de code suivant génère l’avertissement C4373. Pour résoudre ce problème, vous pouvez soit définir le remplacement d’utiliser les qualificateurs CV de mêmes que la fonction membre de base, ou si vous n’aviez pas l’intention de créer un remplacement, vous pouvez donner à la fonction dans la classe dérivée un nom différent.

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
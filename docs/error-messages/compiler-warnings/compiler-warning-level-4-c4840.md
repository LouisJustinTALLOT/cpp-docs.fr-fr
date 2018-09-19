---
title: Du compilateur (niveau 4) d’avertissement C4840 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.topic: error-reference
f1_keywords:
- C4840
dev_langs:
- C++
helpviewer_keywords:
- C4840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c43ce60d319c427877b77a043df7c30bd00edc9b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025878"
---
# <a name="compiler-warning-level-4-c4840"></a>Du compilateur (niveau 4) d’avertissement C4840

> utilisation non portable de la classe*type*» en tant qu’argument à une fonction variadique

## <a name="remarks"></a>Notes

Classes ou structs qui sont passés à une fonction variadique doit être triviale. Quand de tels objets sont passés, le compilateur effectue simplement une copie au niveau du bit et n’appelle pas le constructeur ou le destructeur.

Cet avertissement est disponible à compter de Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère C4840 et montre comment la corriger :

```cpp
// C4840.cpp
// compile by using: cl /EHsc /W4 C4840.cpp
#include <stdio.h>

int main()
{
    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);

    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                       // as an argument to a variadic function
    // To correct the error, you can perform a static cast
    // to convert the object before passing it:
    printf("%i\n", static_cast<int>(s));
}
```

Pour les chaînes générées et gérées à l’aide de `CStringW`, fourni `operator LPCWSTR()` doit être utilisé pour convertir un `CStringW` objet vers le pointeur de chaîne de style C attendu par la chaîne de format :

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
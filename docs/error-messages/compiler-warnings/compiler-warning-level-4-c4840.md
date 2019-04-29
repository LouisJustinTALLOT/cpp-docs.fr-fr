---
title: Du compilateur (niveau 4) d’avertissement C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a757004659c1a9d2ce858cfae5ddfbc6c024d782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360006"
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
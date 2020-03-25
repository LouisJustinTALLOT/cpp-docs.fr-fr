---
title: Avertissement du compilateur (niveau 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: 649083d66d0c7a0ef11c742e56cbfb70e2e9b75f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185202"
---
# <a name="compiler-warning-level-4-c4840"></a>Avertissement du compilateur (niveau 4) C4840

> utilisation non portable de la classe'*type*'en tant qu’argument d’une fonction variadiques

## <a name="remarks"></a>Notes

Les classes ou les structs passés à une fonction variadiques doivent être copiés de façon triviale. Quand de tels objets sont passés, le compilateur effectue simplement une copie au niveau du bit et n’appelle pas le constructeur ou le destructeur.

Cet avertissement est disponible à partir de Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4840 et montre comment la corriger :

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

Pour les chaînes générées et gérées à l’aide de `CStringW`, le `operator LPCWSTR()` fourni doit être utilisé pour effectuer un cast d’un objet `CStringW` vers le pointeur de chaîne de style C attendu par la chaîne de format :

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```

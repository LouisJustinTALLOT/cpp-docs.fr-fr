---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4840'
title: Avertissement du compilateur (niveau 4) C4840
ms.date: 09/13/2018
f1_keywords:
- C4840
helpviewer_keywords:
- C4840
ms.openlocfilehash: a365dc38aff1ab9811407924f7f6e554d91c6f1e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330463"
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

Pour les chaînes générées et gérées à l’aide de `CStringW` , le fourni `operator LPCWSTR()` doit être utilisé pour effectuer un cast d’un `CStringW` objet en pointeur de chaîne de style C attendu par la chaîne de format :

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```

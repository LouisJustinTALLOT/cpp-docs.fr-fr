---
title: __ptr32, __ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: c3ebe642284c6ee269dbfc39985630b7d949435f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179209"
---
# <a name="__ptr32-__ptr64"></a>__ptr32, __ptr64

**Section spécifique de Microsoft**

**__ptr32** représente un pointeur natif sur un système 32 bits, tandis que **__ptr64** représente un pointeur natif sur un système 64 bits.

L'exemple suivant montre comment déclarer chacun de ces types pointeur :

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

Sur un système 32 bits, un pointeur déclaré avec **__ptr64** est tronqué en pointeur 32 bits. Sur un système 64 bits, un pointeur déclaré avec **__ptr32** est converti en pointeur 64 bits.

> [!NOTE]
> Vous ne pouvez pas utiliser **__ptr32** ou **__ptr64** lors de la compilation avec **/clr : pure**. Sinon, l’erreur de compilateur C2472 sera générée. Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas prises en charge dans Visual Studio 2017.

Pour la compatibilité avec les versions précédentes, **_ptr32** et **_ptr64** sont des synonymes pour **__ptr32** et **__ptr64** sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

L’exemple suivant montre comment déclarer et allouer des pointeurs avec les mots clés **__ptr32** et **__ptr64** .

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Types intégrés](../cpp/fundamental-types-cpp.md)

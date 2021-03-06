---
description: 'En savoir plus sur : __sptr, __uptr'
title: __sptr, __uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: 13e365e0e8258c1860df2f107a3dad0ade76e529
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113725"
---
# <a name="__sptr-__uptr"></a>__sptr, __uptr

**Spécifique à Microsoft**

Utilisez le **`__sptr`** **`__uptr`** modificateur ou sur une déclaration de pointeur 32 bits pour spécifier la façon dont le compilateur convertit un pointeur 32 bits en pointeur 64 bits. Un pointeur 32 bits est converti, par exemple, lorsqu'il est assigné à une variable pointeur 64 bits ou est déréférencé sur une plateforme 64 bits.

La documentation Microsoft pour la prise en charge des plateformes 64 bits fait parfois référence au bit le plus significatif d'un pointeur 32 bits comme bit de signe. Par défaut, le compilateur utilise l’extension de signe pour convertir un pointeur 32 bits en pointeur 64 bits. Autrement dit, les 32 bits les moins significatifs du pointeur 64 bits sont définis avec la valeur du pointeur 32 bits et les 32 bits les plus significatifs sont définis avec la valeur du bit de signe du pointeur 32 bits. Cette conversion génère des résultats corrects si le bit de signe est 0, pas si le bit de signe est 1. Par exemple, l'adresse 32 bits 0x7FFFFFFF retourne l'adresse 64 bits équivalente 0x000000007FFFFFFF, mais l'adresse 32 bits 0x80000000 est modifiée incorrectement en 0xFFFFFFFF80000000.

Le **`__sptr`** modificateur, ou pointeur signé, spécifie qu’une conversion de pointeur définit les bits les plus significatifs d’un pointeur 64 bits sur le bit de signe du pointeur 32 bits. Le **`__uptr`** modificateur, ou pointeur non signé, spécifie qu’une conversion affecte la valeur zéro aux bits les plus significatifs. Les déclarations suivantes montrent les **`__sptr`** **`__uptr`** modificateurs et utilisés avec deux pointeurs non qualifiés, deux pointeurs qualifiés avec le type de [__ptr32](../cpp/ptr32-ptr64.md) et un paramètre de fonction.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

Utilisez les **`__sptr`** **`__uptr`** modificateurs et avec les déclarations de pointeur. Utilisez les modificateurs à la position d’un [qualificateur de type pointeur](../c-language/pointer-declarations.md), ce qui signifie que le modificateur doit suivre l’astérisque. Vous ne pouvez pas utiliser les modificateurs avec des [pointeurs vers des membres](../cpp/pointers-to-members.md). Les modificateurs n'ont pas d'incidence sur les déclarations non pointeur.

Pour la compatibilité avec les versions précédentes, **_sptr** et **_uptr** sont des synonymes de **`__sptr`** et, **`__uptr`** sauf si l’option de compilateur [/za désactive les extensions de \( langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="example"></a>Exemple

L’exemple suivant déclare des pointeurs 32 bits qui utilisent les **`__sptr`** **`__uptr`** modificateurs et, assigne chaque pointeur 32 bits à une variable pointeur 64 bits, puis affiche la valeur hexadécimale de chaque pointeur 64 bits. Il est compilé avec le compilateur 64 bits natif et exécuté sur une plateforme 64 bits.

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Modificateurs spécifiques à Microsoft](../cpp/microsoft-specific-modifiers.md)

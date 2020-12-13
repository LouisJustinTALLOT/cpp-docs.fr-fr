---
description: 'En savoir plus sur : avertissement du compilateur (niveaux 1 et 3) C4793'
title: Avertissement du compilateur (niveaux 1 et 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: 00d8a8c3c0537b1960ee287b2ec5fea25491d87e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336026"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>Avertissement du compilateur (niveaux 1 et 3) C4793

> '*fonction*' : la fonction est compilée comme code natif : '*raison*'

## <a name="remarks"></a>Notes

Le compilateur ne peut pas compiler la *fonction* en code managé, même si l’option du compilateur [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) est spécifiée. Au lieu de cela, le compilateur émet un avertissement C4793 et un message de continuation explicatif, puis compile la *fonction* en code natif. Le message de continuation contient le texte de la *raison* qui explique pourquoi la *fonction* ne peut pas être compilée dans `MSIL` .

Il s’agit d’un avertissement de niveau 1 lorsque vous spécifiez l’option de compilateur **/clr : pure** .  L’option de compilateur **/clr : pure** est déconseillée dans visual studio 2015 et n’est pas prise en charge dans visual studio 2017.

Le tableau suivant répertorie tous les messages de continuation possibles.

|Message de raison|Notes|
|--------------------|-------------|
|Les types de données alignés ne sont pas pris en charge dans le code managé|Le CLR doit être en mesure d’allouer des données en fonction des besoins, ce qui peut ne pas être possible si les données sont alignées avec des déclarations telles que [__m128](../../cpp/m128.md) ou [align](../../cpp/align-cpp.md).|
|Les fonctions qui utilisent' __ImageBase’ne sont pas prises en charge dans le code managé|`__ImageBase` est un symbole de l’éditeur de liens spécial qui est généralement utilisé uniquement par du code natif de bas niveau pour charger une DLL.|
|les varargs ne sont pas pris en charge par l’option du compilateur'/CLR'|Les fonctions natives ne peuvent pas appeler des fonctions managées qui ont des [listes d’arguments variables](../../cpp/functions-with-variable-argument-lists-cpp.md) (varargs), car les fonctions ont des exigences de disposition de pile différentes. Toutefois, si vous spécifiez l’option de compilateur **/clr : pure** , les listes d’arguments de variable sont prises en charge, car l’assembly peut contenir uniquement des fonctions managées. Pour plus d’informations, consultez [Code pur et vérifiable (C++/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).|
|Le CLR 64 bits ne prend pas en charge les données déclarées avec le modificateur __ptr32|Un pointeur doit avoir la même taille qu’un pointeur natif sur la plateforme actuelle. Pour plus d’informations, consultez [__ptr32, \_ _ptr64](../../cpp/ptr32-ptr64.md).|
|Le CLR 32 bits ne prend pas en charge les données déclarées avec le modificateur __ptr64|Un pointeur doit avoir la même taille qu’un pointeur natif sur la plateforme actuelle. Pour plus d’informations, consultez [__ptr32, \_ _ptr64](../../cpp/ptr32-ptr64.md).|
|Une ou plusieurs intrinsèques ne sont pas prises en charge dans le code managé|Le nom de l’intrinsèque n’est pas disponible au moment de l’émission du message. Toutefois, un intrinsèque qui provoque ce message représente généralement une instruction machine de bas niveau.|
|L’assembly natif inline (' __asm') n’est pas pris en charge dans le code managé|Le [code assembleur inline](../../assembler/inline/asm.md) peut contenir du code natif arbitraire, qui ne peut pas être géré.|
|Un thunk de fonction virtuelle non __clrcall doit être compilé comme natif|Un thunk de fonction virtuelle non[__clrcall](../../cpp/clrcall.md) doit utiliser une adresse non managée.|
|Une fonction utilisant' _setjmp’doit être compilée en tant que Native|Le CLR doit être en mesure de contrôler l’exécution du programme. Toutefois, la fonction [setjmp](../../cpp/using-setjmp-longjmp.md) contourne l’exécution normale du programme en enregistrant et en restaurant des informations de bas niveau, telles que les registres et l’état d’exécution.|

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4793.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

L’exemple suivant génère l’C4793.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```

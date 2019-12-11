---
title: Avertissement du compilateur (niveaux 3 et 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: a12bee4591df8a7a952dc741c4b26c637bb5256c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991070"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>Avertissement du compilateur (niveaux 3 et 4) C4244

'conversion' : conversion de 'type1' en 'type2', perte possible de données

Un type entier est converti en type entier plus petit. Il s’agit d’un avertissement de niveau 4 Si *type1* est `int` et que *type2* est plus petit que `int`. Dans le cas contraire, il s’agit d’un niveau 3 (une valeur de type [__int64](../../cpp/int8-int16-int32-int64.md) affectée à une variable de type `unsigned int`). Une perte de données peut avoir eu lieu.

Si vous obtenez l'avertissement C4244, vous devez modifier votre programme pour utiliser des types compatibles, ou ajouter une logique à votre code pour garantir que la plage des valeurs possibles sera toujours compatible avec les types que vous utilisez.

L’avertissement C4244 peut également se déclencher au niveau 2. Pour plus d’informations, consultez [Avertissement du compilateur (niveau 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) .

La conversion peut rencontrer un problème dû à des conversions implicites.

L'exemple suivant génère l'avertissement C4244 :

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

Pour plus d’informations, consultez [conversions arithmétiques habituelles](../../c-language/usual-arithmetic-conversions.md).

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

L'avertissement C4244 peut se produire lors de la génération de code pour des cibles 64 bits et ne pas se produire lors de la génération de code pour des cibles 32 bits. Par exemple, une différence entre des pointeurs est une quantité 32 bits sur les plateformes 32 bits mais une quantité 64 bits sur les plateformes 64 bits.

L'exemple suivant génère l'avertissement C4244 lors de la compilation pour des cibles 64 bits :

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```

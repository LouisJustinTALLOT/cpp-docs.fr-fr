---
description: 'En savoir plus sur : pragma de fonction'
title: function (pragma)
ms.date: 08/29/2019
f1_keywords:
- function_CPP
- vc-pragma.function
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
ms.openlocfilehash: 77b215458f9ffdb6be605d0ae4b239451a1fe1bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269300"
---
# <a name="function-pragma"></a>function (pragma)

Indique au compilateur de générer des appels aux fonctions spécifiées dans la liste d’arguments du pragma, au lieu de les incorporer.

## <a name="syntax"></a>Syntaxe

> **#pragma fonction (** *fonction1* [ **,** *fonction2* ...] **)**

## <a name="remarks"></a>Notes

Les fonctions intrinsèques sont normalement générées en tant que code inline, et non en tant qu’appels de fonction. Si vous utilisez le [pragma Intrinsic](intrinsic.md) ou l’option du compilateur [/OI](../build/reference/oi-generate-intrinsic-functions.md) pour indiquer au compilateur de générer des fonctions intrinsèques, vous pouvez utiliser le pragma de **fonction** pour forcer explicitement un appel de fonction. Une fois qu’un pragma de **fonction** est visible, il prend effet à la première définition de fonction contenant une fonction intrinsèque spécifiée. L’effet continue jusqu’à la fin du fichier source, ou à l’apparence d’un `intrinsic` pragma qui spécifie la même fonction intrinsèque. Vous pouvez uniquement utiliser le pragma de **fonction** en dehors d’une fonction, au niveau global.

Pour obtenir la liste des fonctions qui ont des formes intrinsèques, consultez [pragma Intrinsic](intrinsic.md).

## <a name="example"></a>Exemple

```cpp
// pragma_directive_function.cpp
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// use intrinsic forms of memset and strlen
#pragma intrinsic(memset, strlen)

// Find first word break in string, and set remaining
// chars in string to specified char value.
char *set_str_after_word(char *string, char ch) {
   int i;
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */

   for(i = 0; i < len; i++) {
      if (isspace(*(string + i)))
         break;
   }

   for(; i < len; i++)
      *(string + i) = ch;

   return string;
}

// do not use strlen intrinsic
#pragma function(strlen)

// Set all chars in string to specified char value.
char *set_str(char *string, char ch) {
   // Uses intrinsic for memset, but calls strlen library function
   return (char *) memset(string, ch, strlen(string));
}

int main() {
   char *str = (char *) malloc(20 * sizeof(char));

   strcpy_s(str, sizeof("Now is the time"), "Now is the time");
   printf("str is '%s'\n", set_str_after_word(str, '*'));
   printf("str is '%s'\n", set_str(str, '!'));
}
```

```Output
str is 'Now************'
str is '!!!!!!!!!!!!!!!'
```

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

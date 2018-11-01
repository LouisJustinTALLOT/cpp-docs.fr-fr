---
title: Répertorie les fonctions avec des arguments de Variable (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: 1f366af6f4058ffb8356017d59a7c176a978b860
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637301"
---
# <a name="functions-with-variable-argument-lists--c"></a>Répertorie les fonctions avec des arguments de Variable (C++)

Les déclarations de fonction dans lesquelles le dernier membre d’argument-declaration-list est représenté par les points de suspension (...) peuvent prendre une quantité variable d’arguments. Dans ces cas-là, C++ fournit une vérification du type uniquement pour les arguments déclarés explicitement. Vous pouvez utiliser des listes d’arguments variables lorsque vous devez rendre une fonction si générale que même le nombre et les types des arguments peuvent varier. La famille de fonctions est un exemple de fonctions qui utilisent des listes d’arguments variables. `printf` *argument-declaration-list*

## <a name="functions-with-variable-arguments"></a>Fonctions avec des arguments de variables

Pour accéder aux arguments après ceux déclarés, utilisez les macros contenues dans le fichier include standard \<stdarg.h > comme décrit ci-dessous.

**Section spécifique à Microsoft**

Microsoft C++ autorise la spécification de l’ellipse comme argument s’il s’agit du dernier argument et qu’elle est précédée d’une virgule. Par conséquent, la déclaration `int Func( int i, ... );` est conforme, contrairement à `int Func( int i ... );`.

**FIN de la section spécifique à Microsoft**

La déclaration d’une fonction qui accepte une quantité variable d’arguments nécessite au moins un argument d’espace réservé, même si elle n’est pas utilisée. Si cet argument d’espace réservé n’est pas fourni, il est impossible d’accéder aux arguments restants.

Lorsque les arguments de type **char** sont passés comme arguments variables, ils sont convertis en type **int**. De même, lorsque les arguments de type **float** sont passés comme arguments variables, ils sont convertis en type **double**. Les arguments d'autres types sont soumis aux promotions intégrales et à virgule flottante classiques. Consultez [Conversions Standard](standard-conversions.md) pour plus d’informations.

Les fonctions qui requièrent des listes de variables sont déclarées avec des points de suspension (...) dans la liste d’arguments. Utiliser les types et les macros sont décrits dans le \<stdarg.h > fichier include pour accéder aux arguments qui sont passés à une liste de variables. Pour plus d’informations sur ces macros, consultez [va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). dans la documentation de la bibliothèque Runtime C.

L’exemple suivant montre comment les macros fonctionnent avec le type (déclaré dans \<stdarg.h >) :

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

L'exemple ci-dessus illustre les concepts importants suivants :

1. Vous devez établir un marqueur de liste en tant que variable de type `va_list` avant d’accéder à tout argument variable. Dans l'exemple précédent, le marqueur est appelé `vl`.

1. L’accès aux arguments individuels s’effectue à l’aide de la macro `va_arg`. Vous devez indiquer à la macro `va_arg` le type d’argument à extraire afin qu’elle puisse transférer le nombre correct d’octets de la pile. Si vous spécifiez un type incorrect d'une taille différente de celle fournie par le programme appelant à `va_arg`, les résultats sont imprévisibles.

1. Vous devez effectuer un cast explicite du résultat obtenu à l'aide de la macro `va_arg` vers le type souhaité.

Vous devez appeler la macro `va_end` pour terminer le traitement des arguments variables.
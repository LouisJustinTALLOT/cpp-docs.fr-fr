---
title: Extensions Microsoft pour C et C++
ms.date: 06/14/2018
helpviewer_keywords:
- or_eq operator
- ~ operator, extensions to C/C++
- '& operator, extensions to C/C++'
- '&= operator'
- iso646.h header
- Xor operator, Microsoft extensions to C/C++
- '!= operator'
- '! operator, extension to C++'
- Or operator, Microsoft extensions to C/C++
- ^ operator, extensions to C/C++
- ^= operator, C++ extensions
- xor_eq operator
- and_eq operator
- Microsoft extensions to C/C++
- '|= operator'
- '|| operator'
- And operator, extensions to C/C++
- NOT operator
- '&& operator'
- extensions, C language
- Visual C++, extensions to C/C++
- '| operator, extensions'
- not_eq operator
- Visual C, Microsoft extensions
- extensions
- compl method
ms.assetid: e811a74a-45ba-4c00-b206-2f2321b8689a
ms.openlocfilehash: b4025413fcf6389249fc011da020c0cd7c6f4519
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447435"
---
# <a name="microsoft-extensions-to-c-and-c"></a>Extensions Microsoft pour C et C++

Visual C++ étend les normes ANSI C et ANSI C++ comme suit.

## <a name="keywords"></a>Mots clés

Plusieurs mots clés sont ajoutés. Dans la liste dans [mots clés](../../cpp/keywords-cpp.md), les mots clés avec deux traits de soulignement de début sont des extensions de Visual C++.

## <a name="out-of-class-definition-of-static-const-integral-or-enum-members"></a>En dehors de la définition de classe de const integral (ou enum) des membres statiques

Dans le système standard (**/Za**), vous devez vous une définition hors classe pour les membres de données, comme illustré ici :

```cpp
class CMyClass  {
   static const int max = 5;
   int m_array[max];
}
// . . .
const int CMyClass::max;   // out of class definition
```

Sous **/Ze**, la définition hors classe est facultative pour les membres de données statiques, const integral et const enum. Seuls les membres integral et enum qui sont de type static et const peuvent avoir des initialiseurs dans une classe ; l'expression d'initialisation doit être une expression de type const.

Pour éviter des erreurs quand une définition hors classe est fournie dans un en-tête de fichier et le fichier d’en-tête est inclus dans plusieurs fichiers sources, utilisez [selectany](../../cpp/selectany.md). Exemple :

```cpp
__declspec(selectany) const int CMyClass::max = 5;
```

## <a name="casts"></a>Casts

Le compilateur C++ et le compilateur C prennent tous les deux en charge les types de casts non ANSI suivants :

- Casts non ANSI pour produire des valeurs l-value. Exemple :

   ```C
   char *p;
   (( int * ) p )++;
   ```

   > [!NOTE]
   > Cette extension est disponible uniquement dans le langage C. Vous pouvez utiliser le format ANSI C suivant dans le code C++ pour modifier un pointeur comme s'il s'agit d'un pointeur vers un autre type.

   L'exemple précédent peut être réécrit comme suit pour être conforme à la norme ANSI C.

   ```C
   p = ( char * )(( int * )p + 1 );
   ```

- Casts non ANSI d'un pointeur de fonction vers un pointeur de données. Exemple :

   ```C
   int ( * pfunc ) ();
   int *pdata;
   pdata = ( int * ) pfunc;
   ```

   Pour effectuer le même cast tout en conservant la compatibilité ANSI, vous pouvez effectuer un cast du pointeur de fonction vers `uintptr_t` avant d'effectuer un cast de celui-ci vers un pointeur de données :

   ```C
   pdata = ( int * ) (uintptr_t) pfunc;
   ```

## <a name="variable-length-argument-lists"></a>Listes d’arguments de longueur variable

Le compilateur C et le compilateur C++ prennent les tous deux en charge un déclarateur de fonction qui spécifie un nombre variable d’arguments, suivi d’une définition de fonction qui fournit un type à la place :

```cpp
void myfunc( int x, ... );
void myfunc( int x, char * c )
{ }
```

## <a name="single-line-comments"></a>Commentaires à ligne unique

Le compilateur C prend en charge les commentaires sur une seule ligne, qui commencent par deux barres obliques (//) :

```C
// This is a single-line comment.
```

## <a name="scope"></a>Portée

Le compilateur C prend en charge les fonctionnalités suivantes liées à la portée.

- Redéfinitions des éléments extern comme static :

   ```C
   extern int clip();
   static int clip()
   {}
   ```

- Utilisation de redéfinitions typedef bénignes dans la même portée :

   ```C
   typedef int INT;
   typedef int INT;
   ```

- Déclarateurs de fonction ont une portée de fichier :

   ```C
   void func1()
   {
       extern int func2( double );
   }
   int main( void )
   {
       func2( 4 );    //  /Ze passes 4 as type double
   }                  //  /Za passes 4 as type int
   ```

- Utilisation de variables de portée de bloc qui sont initialisées à l'aide d'expressions non constantes :

   ```C
   int clip( int );
   int bar( int );
   int main( void )
   {
       int array[2] = { clip( 2 ), bar( 4 ) };
   }
   int clip( int x )
   {
       return x;
   }
   int bar( int x )
   {
       return x;
   }
   ```

## <a name="data-declarations-and-definitions"></a>Définitions et déclarations de données

Le compilateur C prend en charge les fonctionnalités de définition et de déclaration de données suivantes.

- Constantes de caractère et de chaîne mixtes dans un initialiseur :

   ```C
   char arr[5] = {'a', 'b', "cde"};
   ```

- Champs qui ont des types de base autre que de bits **unsigned int** ou **type signed int**.

- Déclarateurs qui n'ont pas de type :

   ```C
   x;
   int main( void )
   {
       x = 1;
   }
   ```

- Tableaux non dimensionnés comme dernier champ dans les structures et unions :

   ```C
   struct zero
   {
       char *c;
       int zarray[];
   };
   ```

- Structures sans nom (anonymes) :

   ```C
   struct
   {
       int i;
       char *s;
   };
   ```

- Unions sans nom (anonymes) :

   ```C
   union
   {
       int i;
       float fl;
   };
   ```

- Membres sans nom :

   ```C
   struct s
   {
      unsigned int flag : 1;
      unsigned int : 31;
   }
   ```

## <a name="intrinsic-floating-point-functions"></a>Fonctions à virgule flottante intrinsèques

Les deux le x86 du compilateur C++ et le compilateur C prend en charge la génération inline de la `atan`, `atan2`, `cos`, `exp`, `log`, `log10`, `sin`, `sqrt`, et `tan` fonctions lorsque **/Oi** est spécifié. Pour le compilateur C, la conformité ANSI n'est plus assurée quand ces fonctions intrinsèques sont utilisées, car elles ne définissent pas la variable `errno`.

## <a name="passing-a-non-const-pointer-parameter-to-a-function-that-expects-a-reference-to-a-const-pointer-parameter"></a>En passant un paramètre de pointeur non const à une fonction qui attend une référence à un paramètre de pointeur const

Il s’agit d’une extension C++. Ce code est compilé avec **/Ze**:

```cpp
typedef   int   T;

const T  acT = 9;      // A constant of type 'T'
const T* pcT = &acT;   // A pointer to a constant of type 'T'

void func2 ( const T*& rpcT )   // A reference to a pointer to a constant of type 'T'
{
   rpcT = pcT;
}

T*   pT;               // A pointer to a 'T'

void func ()
{
   func2 ( pT );      // Should be an error, but isn't detected
   *pT   = 7;         // Invalidly overwrites the constant 'acT'
}
```

## <a name="iso646h-not-enabled"></a>ISO646. H n’est ne pas activée

Sous **/Ze**, vous devez inclure iso646.h si vous souhaitez utiliser les formulaires de texte des opérateurs suivants :

- && (and)

- &= (and_eq)

- & (bitand)

- &#124;(bitor)

- ~ (compl)

- ! (not)

- ! = (not_eq)

- &#124;&#124;(ou)

- &#124;= (or_eq)

- ^ (xor)

- ^ = (xor_eq)

## <a name="address-of-string-literal-has-type-const-char--not-const-char--"></a>Adresse du littéral de chaîne est de type const char [], non const char (*)]

L’exemple suivant génère `char const (*)[4]` sous **/Za**, mais `char const [4]` sous **/Ze**.

```cpp
#include <stdio.h>
#include <typeinfo>

int main()
{
    printf_s("%s\n", typeid(&"abc").name());
}
```

## <a name="see-also"></a>Voir aussi

- [/Za, /Ze (Désactiver les extensions de langage)](../../build/reference/za-ze-disable-language-extensions.md)
- [Options du compilateur](../../build/reference/compiler-options.md)
- [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)

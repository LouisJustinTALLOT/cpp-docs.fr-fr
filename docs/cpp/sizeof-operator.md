---
title: sizeof, opérateur
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: c9ae581b1b3bea522f2c1557b8be44ee1f32eef1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032289"
---
# <a name="sizeof-operator"></a>sizeof, opérateur

Donne la taille de son opéra en ce qui concerne la taille de **l’omble**de type char .

> [!NOTE]
> Pour plus `sizeof ...` d’informations sur l’opérateur, voir [Ellipsis et modèles variadic](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Notes

Le résultat de la **taille de l’opérateur** est de type `size_t`, un type intégral défini dans le fichier \<incluent stddef.h>. Cet opérateur vous permet d'éviter de spécifier les tailles de données dépendantes de l'ordinateur dans vos programmes.

L’opérande à **la taille peut** être l’une des suivantes:

- Un nom de type. Pour utiliser **la taille d’un** nom de type, le nom doit être inclus entre parenthèses.

- Expression. Lorsqu’il est utilisé avec une expression, **la taille peut** être spécifiée avec ou sans les parenthèses. L'expression n'est pas évaluée.

Lorsque la **taille de l’opérateur** est appliquée à un objet de type **char,** il donne 1. Lorsque la **taille de l’opérateur** est appliquée à un tableau, il donne le nombre total d’octets dans ce tableau, et non la taille du pointeur représenté par l’identifiant de tableau. Pour obtenir la taille du pointeur représenté par l’identifiant de tableau, passez-le comme paramètre à une fonction qui utilise **la taille de**. Par exemple :

## <a name="example"></a>Exemple

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>Exemple de sortie

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

Lorsque la **taille de l’opérateur** est appliquée à une **classe,** **struct**, ou type **de syndicat,** le résultat est le nombre d’octets dans un objet de ce type, plus tout rembourrage ajouté pour aligner les membres sur les limites des mots. Le résultat ne correspond pas forcément à la taille calculée en additionnant les exigences en matière de stockage des membres individuels. L’option de compilation [/Zp](../build/reference/zp-struct-member-alignment.md) et le pragma [pack](../preprocessor/pack.md) affectent les limites d’alignement pour les membres.

La **taille de l’opérateur** ne donne jamais 0, même pour une classe vide.

La **taille de l’opérateur** ne peut pas être utilisée avec les opérands suivants :

- Fonctions. (Toutefois, **la taille peut** être appliquée aux pointeurs aux fonctions.)

- Champ de bits.

- Classes indéfinies.

- Le type **vide**.

- Tableaux alloués de manière dynamique.

- Tableaux externes.

- Types incomplets.

- Noms entre parenthèses de types incomplets.

Lorsque la **taille de l’opérateur** est appliquée à une référence, le résultat est le même que si **la taille avait** été appliquée à l’objet lui-même.

Si un tableau non dimensionné est le dernier élément d’une structure, la **taille de l’opérateur** retourne la taille de la structure sans le tableau.

La **taille de l’opérateur** est souvent utilisée pour calculer le nombre d’éléments dans un tableau à l’aide d’une expression de la forme :

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)

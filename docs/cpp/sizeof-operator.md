---
title: sizeof, opérateur
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: bc1165cf1df3933575013906d1b24673467f0b36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178715"
---
# <a name="sizeof-operator"></a>sizeof, opérateur

Produit la taille de son opérande par rapport à la taille du type **char**.

> [!NOTE]
>  Pour plus d’informations sur l’opérateur `sizeof ...`, consultez [ellipses et modèles variadiques](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Notes

Le résultat de l’opérateur **sizeof** est de type `size_t`, un type intégral défini dans le fichier include \<STDDEF. h >. Cet opérateur vous permet d'éviter de spécifier les tailles de données dépendantes de l'ordinateur dans vos programmes.

L’opérande de **sizeof** peut être l’un des suivants :

- Un nom de type. Pour utiliser **sizeof** avec un nom de type, le nom doit être placé entre parenthèses.

- Expression. En cas d’utilisation avec une expression, **sizeof** peut être spécifié avec ou sans parenthèses. L'expression n'est pas évaluée.

Lorsque l’opérateur **sizeof** est appliqué à un objet de type **char**, il génère 1. Lorsque l’opérateur **sizeof** est appliqué à un tableau, il produit le nombre total d’octets dans ce tableau, et non la taille du pointeur représenté par l’identificateur de tableau. Pour obtenir la taille du pointeur représenté par l’identificateur de tableau, transmettez-le en tant que paramètre à une fonction qui utilise **sizeof**. Par exemple :

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

Lorsque l’opérateur **sizeof** est appliqué à un type de **classe**, de **struct**ou d' **Union** , le résultat est le nombre d’octets dans un objet de ce type, plus tout remplissage ajouté pour aligner les membres sur les limites de mots. Le résultat ne correspond pas forcément à la taille calculée en additionnant les exigences en matière de stockage des membres individuels. L’option de compilateur [/ZP](../build/reference/zp-struct-member-alignment.md) et le pragma [Pack](../preprocessor/pack.md) affectent les limites d’alignement pour les membres.

L’opérateur **sizeof** ne produit jamais la valeur 0, même pour une classe vide.

L’opérateur **sizeof** ne peut pas être utilisé avec les opérandes suivants :

- Fonctions. (Toutefois, **sizeof** peut être appliqué aux pointeurs vers des fonctions.)

- Champ de bits.

- Classes indéfinies.

- Type **void**.

- Tableaux alloués de manière dynamique.

- Tableaux externes.

- Types incomplets.

- Noms entre parenthèses de types incomplets.

Lorsque l’opérateur **sizeof** est appliqué à une référence, le résultat est le même que si **sizeof** avait été appliqué à l’objet lui-même.

Si un tableau non dimensionné est le dernier élément d’une structure, l’opérateur **sizeof** retourne la taille de la structure sans le tableau.

L’opérateur **sizeof** est souvent utilisé pour calculer le nombre d’éléments dans un tableau à l’aide d’une expression de la forme suivante :

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)

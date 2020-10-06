---
title: Expressions primaires
description: Expressions primaires dans le langage de programmation C++.
ms.date: 10/02/2020
helpviewer_keywords:
- primary expressions
- expressions [C++], name
- expressions [C++], literal
- expressions [C++], primary
- expressions [C++], qualified names
ms.assetid: 8ef9a814-6058-4b93-9b6e-e8eb8350b1ca
ms.openlocfilehash: 4c52992071453bc189a3078db9592b02dfb8ba9b
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765330"
---
# <a name="primary-expressions"></a>Expressions primaires

Les expressions primaires sont des blocs de construction d'expressions plus complexes. Il peut s’agir de littéraux, de noms et de noms qualifiés par l’opérateur de résolution de portée ( `::` ). Une expression primaire peut prendre chacune des formes suivantes :

*`primary-expression`*\
&emsp;*`literal`*\
&emsp;**`this`**\
&emsp;*`name`*\
&emsp;**`::`** *`name`* **`(`** *`expression`* **`)`**

Un *`literal`* est une expression primaire constante. Son type dépend de la forme de sa spécification. Pour obtenir des informations complètes sur la spécification de littéraux, consultez [littéraux](../cpp/numeric-boolean-and-pointer-literals-cpp.md) .

Le **`this`** mot clé est un pointeur vers un objet de classe. Elle est disponible dans les fonctions membres non statiques. Il pointe vers l’instance de la classe pour laquelle la fonction a été appelée. Le **`this`** mot clé ne peut pas être utilisé en dehors du corps d’une fonction membre de classe.

Le type du **`this`** pointeur est `type * const` (où `type` est le nom de la classe) dans les fonctions qui ne modifient pas spécifiquement le **`this`** pointeur. L’exemple suivant montre des déclarations de fonctions membres et les types de **`this`** :

```cpp
// expre_Primary_Expressions.cpp
// compile with: /LD
class Example
{
public:
    void Func();          //  * const this
    void Func() const;    //  const * const this
    void Func() volatile; //  volatile * const this
};
```

Pour plus d’informations sur la modification du type du **`this`** pointeur, consultez [ `this` pointeur](this-pointer.md).

L’opérateur de résolution de portée ( **`::`** ) suivi d’un nom est une expression primaire.  Ces noms doivent être des noms au niveau de la portée globale, pas des noms de membres. Le type de l’expression est déterminé par la déclaration du nom. Il s’agit d’une l-value (autrement dit, elle peut apparaître sur le côté gauche d’une expression d’assignation) si le nom de déclaration est une l-value. L’opérateur résolution-portée permet de faire référence à un nom global, même si ce nom est masqué dans la portée actuelle. Consultez [scope](../cpp/scope-visual-cpp.md) pour obtenir un exemple d’utilisation de l’opérateur de résolution de portée.

Une expression entre parenthèses est une expression primaire. Son type et sa valeur sont identiques au type et à la valeur de l’expression non entre parenthèses. Il s’agit d’une l-value si l’expression non entre parenthèses est une l-value.

Les exemples d'expressions principaux incluent :

```cpp
100 // literal
'c' // literal
this // in a member function, a pointer to the class instance
::func // a global function
::operator + // a global operator function
::A::B // a global qualified name
( i + 1 ) // a parenthesized expression
```

Ces exemples sont tous considérés comme des *noms*et, en tant que tels, des expressions primaires, sous différentes formes :

```cpp
MyClass // an identifier
MyClass::f // a qualified name
operator = // an operator function name
operator char* // a conversion operator function name
~MyClass // a destructor name
A::B   // a qualified name
A<int> // a template id
```

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)

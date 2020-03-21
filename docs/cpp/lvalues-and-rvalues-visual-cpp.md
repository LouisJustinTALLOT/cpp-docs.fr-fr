---
title: 'Catégories de valeurs : lvalues et rvaluesC++()'
ms.date: 05/07/2019
helpviewer_keywords:
- R-values [C++]
- L-values [C++]
ms.assetid: a8843344-cccc-40be-b701-b71f7b5cdcaf
ms.openlocfilehash: 23625ddf44d16a4dc408b87f27b9cdfba7a9cbd4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077236"
---
# <a name="lvalues-and-rvalues-c"></a>Lvalues et Rvalues (C++)

Chaque C++ expression a un type et appartient à une *catégorie de valeur*. Les catégories de valeur constituent la base des règles que les compilateurs doivent suivre lors de la création, de la copie et du déplacement d’objets temporaires lors de l’évaluation de l’expression.

La norme C++ 17 définit les catégories de valeurs d’expression comme suit :

- Un *glvalue* est une expression dont l’évaluation détermine l’identité d’un objet, d’un champ de bits ou d’une fonction.
- Un *prvalue* est une expression dont l’évaluation Initialise un objet ou un champ de bits, ou calcule la valeur de l’opérande d’un opérateur, comme spécifié par le contexte dans lequel il apparaît.
- Un *xValue* est un glvalue qui désigne un objet ou un champ de bits dont les ressources peuvent être réutilisées (généralement parce qu’il est proche de la fin de sa durée de vie). Exemple : certains genres d’expressions qui impliquent des références rvalue (8.3.2) génèrent des x, par exemple un appel à une fonction dont le type de retour est une référence rvalue ou un cast en un type de référence rvalue.
- Une *lvalue* est un glvalue qui n’est pas un XValue.
- Une *rvalue* est un prvalue ou un XValue.

Le diagramme suivant illustre les relations entre les catégories :

![C++catégories de valeurs d’expression](media/value_categories.png "C++catégories de valeurs d’expression")

Une lvalue a une adresse à laquelle votre programme peut accéder. Les noms de variables, y compris les variables **const** , les éléments de tableau, les appels de fonction qui retournent une référence lvalue, les champs de bits, les unions et les membres de classe sont des exemples d’expressions lvalue.

Une expression prvalue n’a pas d’adresse qui est accessible par votre programme. Les littéraux, les appels de fonction qui retournent un type non-référence et les objets temporaires créés pendant l’expression évaluation, sont des exemples d’expressions prvalue.

Une expression XValue a une adresse qui n’est plus accessible par votre programme, mais qui peut être utilisée pour initialiser une référence rvalue, qui fournit l’accès à l’expression. Les exemples incluent des appels de fonctions qui retournent une référence rvalue, et l’indice de tableau, le membre et le pointeur vers des expressions de membre où le tableau ou l’objet est une référence rvalue.

## <a name="example"></a>Exemple

L'exemple suivant illustre plusieurs utilisations correctes et incorrectes des valeurs lvalues et des rvalues :

```cpp
// lvalues_and_rvalues2.cpp
int main()
{
    int i, j, *p;

    // Correct usage: the variable i is an lvalue and the literal 7 is a prvalue.
    i = 7;

    // Incorrect usage: The left operand must be an lvalue (C2106).`j * 4` is a prvalue.
    7 = i; // C2106
    j * 4 = 7; // C2106

    // Correct usage: the dereferenced pointer is an lvalue.
    *p = i;

    // Correct usage: the conditional operator returns an lvalue.
    ((i < 3) ? i : j) = 7;

    // Incorrect usage: the constant ci is a non-modifiable lvalue (C3892).
    const int ci = 7;
    ci = 9; // C3892
}
```

> [!NOTE]
> Les exemples de cette rubrique illustrent une utilisation correcte et incorrecte lorsque les opérateurs ne sont pas surchargés. En surchargeant les opérateurs, vous pouvez faire d'une expression telle que `j * 4` une lvalue.

Les termes *lvalue* et *rvalue* sont souvent utilisés lorsque vous faites référence à des références d’objet. Pour plus d’informations sur les références, consultez [déclarateur de référence lvalue : &](../cpp/lvalue-reference-declarator-amp.md) et le [déclarateur de référence Rvalue : & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)<br/>
[Déclarateur de référence Lvalue : &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Déclarateur de référence Rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md)

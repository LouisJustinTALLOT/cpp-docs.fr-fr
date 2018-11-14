---
title: Opérateurs de multiplication et opérateur modulo
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
ms.openlocfilehash: 9a01672976703634c06724c9c655605bb433facf
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330383"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>Opérateurs de multiplication et opérateur modulo

## <a name="syntax"></a>Syntaxe

```
expression * expression
expression / expression
expression % expression
```

## <a name="remarks"></a>Notes

Les opérateurs de multiplication sont :

- Multiplication (<strong>\**</strong>)

- Division (**/**)

- Modulo (reste de division) (**%**)

Ces opérateurs binaires ont une associativité de droite à gauche.

Les opérateurs de multiplication prennent des opérandes de types arithmétiques. L’opérateur modulo (**%**) a une exigence plus stricte dans la mesure où ses opérandes doivent être de type intégral. (Pour obtenir le reste d’une division à virgule flottante, utilisez la fonction de l’exécution, [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Les conversions abordées dans [Conversions Standard](standard-conversions.md) sont appliquées aux opérandes, et le résultat est du type converti.

L’opérateur de multiplication montre le résultat de la multiplication du premier opérande par le second.

L’opérateur de division montre le résultat de la division du premier opérande par le second.

L’opérateur modulo Obtient le reste donné par l’expression suivante, où *e1* est le premier opérande et *e2* est le deuxième : *e1* -(*e1*  /  *e2*) \* *e2*, où les deux opérandes sont des types intégraux.

La division par 0 dans une division ou une expression de modulo est éliminée et provoque une erreur d'exécution. Par conséquent, les expressions suivantes génèrent des résultats indéterminés et erronés :

```cpp
i % 0
f / 0.0
```

Si les deux opérandes pour une expression de multiplication, de division ou de modulo ont le même signe, le résultat est positif. Sinon, le résultat est négative. Le résultat du signe d'une opération modulo est défini par l'implémentation.

> [!NOTE]
>  Étant donné que les conversions exécutées par les opérateurs de multiplication ne fournissent pas de conditions de dépassement de capacité positif ou de dépassement de capacité négatif, les informations peuvent être perdues si le résultat d'une opération de multiplication ne peut pas être représenté dans le type des opérandes après conversion.

**Section spécifique à Microsoft**

Dans Microsoft C++, le résultat d’une expression de modulo est toujours le même que le signe du premier opérande.

**FIN de la section spécifique à Microsoft**

Si la division calculée de deux entiers est incorrecte et qu’un seul opérande est négatif, le résultat est le plus grand entier (en amplitude, sans tenir compte du signe) qui est inférieur à la valeur exacte que l’opérateur de division produirait. Par exemple, la valeur calculée de -11 / 3 est-3.666666666. Le résultat de cette division intégrale est -3.

La relation entre les opérateurs de multiplication est indiquée par l’identité (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*.

## <a name="example"></a>Exemple

Le programme suivant montre les opérateurs de multiplication. Notez que des opérandes de `10 / 3` doit être explicitement converti en type **float** pour éviter la troncation afin que les deux opérandes sont de type **float** avant la division.

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs binaires](../cpp/expressions-with-binary-operators.md)<br/>
[Opérateurs intégrés, priorité et associativité C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Opérateurs de multiplication C](../c-language/c-multiplicative-operators.md)
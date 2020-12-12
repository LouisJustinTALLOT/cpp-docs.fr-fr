---
description: 'En savoir plus sur : opérateurs de multiplication et opérateur modulo'
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
ms.openlocfilehash: e3e3e3823abb255922bf31be90b4a116fb100efe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313864"
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

- Multiplication ( <strong>\*</strong> )

- Division ( **/** )

- Modulo (reste de la Division) ( **%** )

Ces opérateurs binaires ont une associativité de droite à gauche.

Les opérateurs de multiplication prennent des opérandes de types arithmétiques. L’opérateur modulo ( **%** ) a une exigence plus stricte en ce que ses opérandes doivent être de type intégral. (Pour obtenir le reste d’une division à virgule flottante, utilisez la fonction runtime, [fmod](../c-runtime-library/reference/fmod-fmodf.md).) Les conversions couvertes dans les [conversions standard](standard-conversions.md) sont appliquées aux opérandes, et le résultat est du type converti.

L'opérateur de multiplication montre le résultat de la multiplication du premier opérande par le second.

L’opérateur de division montre le résultat de la division du premier opérande par le second.

L’opérateur modulo produit le reste donné par l’expression suivante, où *E1* est le premier opérande et *E2* le second : *E1* -(*E1*  /  *E2*) \* *E2*, où les deux opérandes sont des types intégraux.

La division par 0 dans une division ou une expression de modulo est éliminée et provoque une erreur d'exécution. Par conséquent, les expressions suivantes génèrent des résultats indéterminés et erronés :

```cpp
i % 0
f / 0.0
```

Si les deux opérandes pour une expression de multiplication, de division ou de modulo ont le même signe, le résultat est positif. Sinon, le résultat est négative. Le résultat du signe d'une opération modulo est défini par l'implémentation.

> [!NOTE]
> Étant donné que les conversions exécutées par les opérateurs de multiplication ne fournissent pas de conditions de dépassement de capacité positif ou de dépassement de capacité négatif, les informations peuvent être perdues si le résultat d'une opération de multiplication ne peut pas être représenté dans le type des opérandes après conversion.

**Spécifique à Microsoft**

Dans Microsoft C++, le résultat d'une expression de modulo est toujours le même que le signe du premier opérande.

**FIN spécifique à Microsoft**

Si la division calculée de deux entiers est incorrecte et qu'un seul opérande est négatif, le résultat est le plus grand entier (en amplitude, sans tenir compte du signe) qui est inférieur à la valeur exacte que l'opérateur de division produirait. Par exemple, la valeur calculée de-11/3 est-3,666666666. Le résultat de cette division intégrale est-3.

La relation entre les opérateurs de multiplication est donnée par l’identité (*E1*  /  *E2*) \* *E2*  +  *E1 E1*  %    ==  *E1*.

## <a name="example"></a>Exemple

Le programme suivant montre les opérateurs de multiplication. Notez que l’un des opérandes de `10 / 3` doit être explicitement casté en type **`float`** pour éviter la troncation afin que les deux opérandes soient de type **`float`** avant la Division.

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

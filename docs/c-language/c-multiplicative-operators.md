---
description: 'En savoir plus sur : opérateurs de multiplication C'
title: Opérateurs de multiplication C
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
ms.openlocfilehash: 61689435c5e76238feba26d5a49ffe3530798f88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300266"
---
# <a name="c-multiplicative-operators"></a>Opérateurs de multiplication C

Les opérateurs de multiplication effectuent des opérations de multiplication ( <strong>\*</strong> ), de division ( **/** ) et de reste ( **%** ).

## <a name="syntax"></a>Syntaxe

multiplicatif *-* expression : cast-expression multiplicatif-expression cast-expression cast-expression multiplicative-expression cast-expression cast-expression cast-expression &nbsp; &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp; &nbsp;  <strong>\*</strong>  &nbsp; &nbsp; &nbsp; &nbsp;  **/**  &nbsp; &nbsp; &nbsp; &nbsp;  **%** 

Les opérandes de l’opérateur de reste ( **%** ) doivent être intégraux. Les opérateurs de multiplication ( <strong>\*</strong> ) et de division ( **/** ) peuvent prendre des opérandes de type intégral ou flottant ; les types des opérandes peuvent être différents.

Les opérateurs de multiplication exécutent les conversions arithmétiques courantes sur les opérandes. Le type du résultat est le type des opérandes après conversion.

> [!NOTE]
> Étant donné que les conversions exécutées par les opérateurs de multiplication ne fournissent pas de conditions de dépassement de capacité positif ou de dépassement de capacité négatif, les informations peuvent être perdues si le résultat d'une opération de multiplication ne peut pas être représenté dans le type des opérandes après conversion.

Les opérateurs de multiplication C sont décrits ci-dessous :

|Opérateur|Description|
|--------------|-----------------|
|<strong>\*</strong>|L’opérateur de multiplication provoque la multiplication de ces deux opérandes.|
|**/**|L’opérateur de division provoque la division du premier opérande par le deuxième. Si deux opérandes entiers sont divisés et que le résultat n’est pas un entier, il est tronqué selon les règles suivantes :<br/><br/>- Le résultat de la division par 0 est indéfini selon la norme C ANSI. Le compilateur Microsoft C génère une erreur au moment de la compilation ou de l'exécution.<br/><br/>- Si les deux opérandes sont positifs ou non signés, le résultat est tronqué vers 0.<br/><br/>- Si l’un des opérandes est négatif, si le résultat de l’opération est le plus grand entier inférieur ou égal au quotient algébrique ou le plus petit entier supérieur ou égal au quotient algébrique, l’implémentation est définie. (Consultez la section spécifique à Microsoft ci-dessous.)|
|**%**|Le résultat de l’opérateur de reste est le reste lorsque le premier opérande est divisé par le deuxième. Lorsque la division est incorrecte, le résultat est déterminé par les règles suivantes :<br/><br/>- Si l’opérande de droite est zéro, le résultat est non défini.<br/><br/>- Si les deux opérandes sont positifs ou non signés, le résultat est positif.<br/><br/>- Si l’un des opérandes est négatif et que le résultat est incorrect, le résultat est que l’implémentation est définie. (Consultez la section spécifique à Microsoft ci-dessous.)|

### <a name="microsoft-specific"></a>Spécifique à Microsoft

Dans la division où l’un des opérandes est négatif, la direction de la troncation est vers 0.

Si l’une ou l’autre opération est négative dans la division avec l’opérateur de reste, le résultat a la même signature que le dividende (le premier opérande de l’expression).

## <a name="examples"></a>Exemples

Les déclarations illustrées ci-dessous sont utilisées pour les exemples suivants :

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

Cette instruction utilise l'opérateur de multiplication :

```
y = x * i;
```

Dans ce cas, `x` est multiplié par `i` pour donner la valeur 20,0. Le résultat a le **`double`** type.

```
n = i / j;
```

Dans cet exemple, 10 est divisé par 3. Le résultat est tronqué vers 0, ce qui produit la valeur entière 3.

```
n = i % j;
```

Cette instruction assigne le reste entier `n` lorsque 10 est divisé par 3.

**Spécifique à Microsoft**

Le signe du reste est identique au signe du dividende. Par exemple :

```
50 % -6 = 2
-50 % 6 = -2
```

Dans chaque cas, `50` et `2` ont le même signe.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Opérateurs de multiplication et opérateur modulo](../cpp/multiplicative-operators-and-the-modulus-operator.md)

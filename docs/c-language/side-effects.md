---
description: 'En savoir plus sur : effets secondaires'
title: Effets secondaires
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
ms.openlocfilehash: 78a08cb2c6290a3cb9c0c61a714cb2bcfe61a4cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292778"
---
# <a name="side-effects"></a>Effets secondaires

L'ordre d'évaluation des expressions est défini par l'implémentation spécifique, sauf lorsque le langage garantit un ordre d'évaluation particulier (comme décrit dans [Priorité et ordre d'évaluation](../c-language/precedence-and-order-of-evaluation.md)). Par exemple, des effets secondaires se produisent dans les appels de fonction suivants :

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

Les arguments d'un appel de fonction peuvent être évalués dans n'importe quel ordre. L'expression `i + 1` peut être évaluée avant `i = j + 2`, ou `i = j + 2` peut être évaluée avant `i + 1`. Le résultat diffère à chaque fois. De même, il est impossible de garantir quels caractères sont passés réellement à `myproc`. Étant donné que les opérations d'incrémentation et de décrémentation unaires impliquent des assignations, ces opérations peuvent provoquer des effets secondaires, comme illustré dans l'exemple suivant :

```
x[i] = i++;
```

Dans cet exemple, la valeur de `x` modifiée est imprévisible. La valeur de l'indice peut être la nouvelle ou l'ancienne valeur de `i`. Le résultat peut varier selon le compilateur ou le niveau d'optimisation.

Comme C ne définit pas l'ordre d'évaluation des effets secondaires, les deux méthodes d'évaluation abordées ci-dessus sont correctes et peuvent être implémentées. Pour vous assurer que votre code est portable et clair, évitez les instructions qui dépendent d'un ordre d'évaluation particulier pour les effets secondaires.

## <a name="see-also"></a>Voir aussi

[Évaluation d’expression](../c-language/expression-evaluation-c.md)

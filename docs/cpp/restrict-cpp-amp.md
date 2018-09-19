---
title: restreindre (C++ AMP) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- cpu_CPP
- amp_CPP
dev_langs:
- C++
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77ca639b5eaf6a0569f1fe678af741ccad58c0d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116683"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Le spécificateur de restriction peut être appliqué aux déclarations de fonctions et lambda. Il applique des restrictions au code dans la fonction et sur le comportement de cette fonction dans les applications qui utilisent le runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
>  Pour plus d’informations sur la **restreindre** mot clé qui fait partie de la **__declspec** attributs de classe de stockage, consultez [restreindre](../cpp/restrict.md).

Le **restreindre** clause prend les formes suivantes :

|Clause|Description|
|------------|-----------------|
|`restrict(cpu)`|La fonction peut utiliser le langage C++ complet. Seules les autres fonctions déclarées en utilisant des fonctions restrict(cpu) peuvent appeler la fonction.|
|`restrict(amp)`|La fonction peut uniquement utiliser le sous-ensemble du langage C++ que C++ AMP peut accélérer.|
|Séquence de clauses `restrict(cpu)` et `restrict(amp)`|La fonction doit adhérer aux limitations des clauses `restrict(cpu)` et `restrict(amp)`. La fonction peut être appelée par les fonctions déclarées au moyen de `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` ou `restrict(amp, cpu)`.<br /><br /> L'expression `restrict(A) restrict(B)` peut être écrite `restrict(A,B)`.|

## <a name="remarks"></a>Notes

Le **restreindre** mot clé est un mot clé contextuel. Les spécificateurs de restrictions, `cpu` et `amp`, ne sont pas des mots réservés. La liste des spécificateurs n'est pas extensible. Une fonction qui n’a pas un **restreindre** clause est identique à une fonction qui a le `restrict(cpu)` clause.

Une fonction qui possède la clause `restrict(amp)` présente les limitations suivantes :

- La fonction peut appeler uniquement des fonctions qui possèdent la clause `restrict(amp)`.

- La fonction doit être en mesure d'être inline.

- La fonction peut déclarer uniquement **int**, **unsigned int**, **float**, et **double** variables et les classes et les structures qui contiennent uniquement ces types. **bool** est également autorisé, mais il doit être aligné à 4 octets si vous l’utilisez dans un type composite.

- Les fonctions lambda ne peuvent pas capturer par référence et ne peuvent pas capturer les pointeurs.

- Les références et les pointeurs à une seule indirection sont pris en charge uniquement en tant que variables locales, arguments de fonction ou types de retour.

- Les éléments suivants ne sont pas autorisés :

   - récurrence,

   - Les variables déclarées avec le [volatile](../cpp/volatile-cpp.md) mot clé.

   - fonctions virtuelles,

   - pointeurs désignant des fonctions,

   - pointeurs désignant des fonctions membres,

   - pointeurs dans des structures,

   - pointeurs désignant des pointeurs,

   - **GoTo** instructions.

   - instructions étiquetées,

   - **Essayez**, **catch**, ou **lever** instructions.

   - Variables globales.

   - variables statiques Utilisez [tile_static, mot clé](../cpp/tile-static-keyword.md) à la place.

   - **dynamic_cast** casts.

   - Le **typeid** opérateur.

   - déclarations asm,

   - varargs.

Pour une présentation des limitations des fonctions, consultez [restreindre les Restrictions (amp)](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `restrict(amp)`clause.

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
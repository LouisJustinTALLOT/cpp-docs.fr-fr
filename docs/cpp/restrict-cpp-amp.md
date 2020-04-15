---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 5a0011d11e4a59c9ca3a5e18f44d4cf831b21582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366648"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Le spécificateur de restriction peut être appliqué aux déclarations de fonctions et lambda. Il applique des restrictions au code dans la fonction et sur le comportement de cette fonction dans les applications qui utilisent le runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Pour plus d’informations sur le mot clé **de restriction** qui fait partie des attributs de classe de stockage **__declspec,** voir [restreindre](../cpp/restrict.md).

La clause **de restriction** prend les formes suivantes :

|Clause|Description|
|------------|-----------------|
|`restrict(cpu)`|La fonction peut utiliser le langage C++ complet. Seules les autres fonctions déclarées en utilisant des fonctions restrict(cpu) peuvent appeler la fonction.|
|`restrict(amp)`|La fonction peut uniquement utiliser le sous-ensemble du langage C++ que C++ AMP peut accélérer.|
|Séquence de clauses `restrict(cpu)` et `restrict(amp)`|La fonction doit adhérer aux limitations des clauses `restrict(cpu)` et `restrict(amp)`. La fonction peut être appelée par les fonctions déclarées au moyen de `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` ou `restrict(amp, cpu)`.<br /><br /> L'expression `restrict(A) restrict(B)` peut être écrite `restrict(A,B)`.|

## <a name="remarks"></a>Notes

Le mot clé **restrictif** est un mot clé contextuel. Les spécificateurs de restrictions, `cpu` et `amp`, ne sont pas des mots réservés. La liste des spécificateurs n'est pas extensible. Une fonction qui n’a pas de clause **de** `restrict(cpu)` restriction est la même qu’une fonction qui comporte la clause.

Une fonction qui possède la clause `restrict(amp)` présente les limitations suivantes :

- La fonction peut appeler uniquement des fonctions qui possèdent la clause `restrict(amp)`.

- La fonction doit être en mesure d'être inline.

- La fonction ne peut déclarer que **l’int,** **int non signé,** **flotter,** et les variables **doubles,** et les classes et les structures qui ne contiennent que ces types. **bool** est également autorisé, mais il doit être 4-byte-aligné si vous l’utilisez dans un type composé.

- Les fonctions lambda ne peuvent pas capturer par référence et ne peuvent pas capturer les pointeurs.

- Les références et les pointeurs à une seule indirection sont pris en charge uniquement en tant que variables locales, arguments de fonction ou types de retour.

- Les éléments suivants ne sont pas autorisés :

  - récurrence,

  - Variables déclarées avec le mot clé [volatil.](../cpp/volatile-cpp.md)

  - fonctions virtuelles,

  - pointeurs désignant des fonctions,

  - pointeurs désignant des fonctions membres,

  - pointeurs dans des structures,

  - pointeurs désignant des pointeurs,

  - **goto** déclarations.

  - instructions étiquetées,

  - **essayer,** **attraper,** ou **lancer des** déclarations.

  - Variables globales.

  - variables statiques Utilisez [tile_static mot clé à](../cpp/tile-static-keyword.md) la place.

  - **dynamic_cast** jette.

  - **L’opérateur typeid.**

  - déclarations asm,

  - varargs.

Pour une discussion sur les limitations de la fonction, voir [restreindre (amp) Restrictions](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/).

## <a name="example"></a>Exemple

L’exemple suivant montre `restrict(amp)`comment utiliser la clause.

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

---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: b3464b758c6b66cdbd5015ee4b7c9d11eb2209dd
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404936"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Le spécificateur de restriction peut être appliqué aux déclarations de fonctions et lambda. Il applique des restrictions au code dans la fonction et sur le comportement de cette fonction dans les applications qui utilisent le runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Pour plus d’informations sur le mot clé **restrict** qui fait partie des attributs de classe de stockage **__declspec** , consultez [restreindre](../cpp/restrict.md).

La clause **restrict** prend les formes suivantes :

|Clause|Description|
|------------|-----------------|
|`restrict(cpu)`|La fonction peut utiliser le langage C++ complet. Seules les autres fonctions déclarées en utilisant des fonctions restrict(cpu) peuvent appeler la fonction.|
|`restrict(amp)`|La fonction peut uniquement utiliser le sous-ensemble du langage C++ que C++ AMP peut accélérer.|
|Séquence de clauses `restrict(cpu)` et `restrict(amp)`|La fonction doit adhérer aux limitations des clauses `restrict(cpu)` et `restrict(amp)`. La fonction peut être appelée par les fonctions déclarées au moyen de `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` ou `restrict(amp, cpu)`.<br /><br /> L'expression `restrict(A) restrict(B)` peut être écrite `restrict(A,B)`.|

## <a name="remarks"></a>Notes

Le mot clé **restrict** est un mot clé contextuel. Les spécificateurs de restrictions, `cpu` et `amp`, ne sont pas des mots réservés. La liste des spécificateurs n'est pas extensible. Une fonction qui n’a pas de clause **restrict** est identique à une fonction qui possède la `restrict(cpu)` clause.

Une fonction qui possède la clause `restrict(amp)` présente les limitations suivantes :

- La fonction peut appeler uniquement des fonctions qui possèdent la clause `restrict(amp)`.

- La fonction doit être en mesure d'être inline.

- La fonction peut déclarer uniquement des variables **int**, **unsigned int**, **float**et **double** , ainsi que des classes et des structures qui contiennent uniquement ces types. **bool** est également autorisé, mais il doit être aligné sur 4 octets si vous l’utilisez dans un type composé.

- Les fonctions lambda ne peuvent pas capturer par référence et ne peuvent pas capturer les pointeurs.

- Les références et les pointeurs à une seule indirection sont pris en charge uniquement en tant que variables locales, arguments de fonction ou types de retour.

- Les éléments suivants ne sont pas autorisés :

  - récurrence,

  - Variables déclarées avec le mot clé [volatile](../cpp/volatile-cpp.md) .

  - fonctions virtuelles,

  - pointeurs désignant des fonctions,

  - pointeurs désignant des fonctions membres,

  - pointeurs dans des structures,

  - pointeurs désignant des pointeurs,

  - instructions **goto** .

  - instructions étiquetées,

  - instructions **try**, **catch**ou **throw** .

  - Variables globales.

  - variables statiques Utilisez à la place le [mot clé tile_static](../cpp/tile-static-keyword.md) .

  - **dynamic_cast** casts.

  - Opérateur **typeid** .

  - déclarations asm,

  - varargs.

Pour plus d’informations sur les limitations relatives aux fonctions, consultez [restrictions (amp)](/archive/blogs/nativeconcurrency/restrictamp-restrictions-part-0-of-n-introduction).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `restrict(amp)` clause.

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

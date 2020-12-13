---
description: 'En savoir plus sur : Restrict (C++ AMP)'
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 928d4f9dde9421d2c5ab244af26a688a9828881e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151449"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

Le spécificateur de restriction peut être appliqué aux déclarations de fonctions et lambda. Il applique des restrictions au code dans la fonction et sur le comportement de cette fonction dans les applications qui utilisent le runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Pour plus d’informations sur le **`restrict`** mot clé qui fait partie des **`__declspec`** attributs de classe de stockage, consultez [restreindre](../cpp/restrict.md).

La **`restrict`** clause prend les formes suivantes :

|Clause|Description|
|------------|-----------------|
|`restrict(cpu)`|La fonction peut utiliser le langage C++ complet. Seules les autres fonctions déclarées en utilisant des fonctions restrict(cpu) peuvent appeler la fonction.|
|`restrict(amp)`|La fonction peut uniquement utiliser le sous-ensemble du langage C++ que C++ AMP peut accélérer.|
|Séquence de clauses `restrict(cpu)` et `restrict(amp)`|La fonction doit adhérer aux limitations des clauses `restrict(cpu)` et `restrict(amp)`. La fonction peut être appelée par les fonctions déclarées au moyen de `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` ou `restrict(amp, cpu)`.<br /><br /> L'expression `restrict(A) restrict(B)` peut être écrite `restrict(A,B)`.|

## <a name="remarks"></a>Notes

Le **`restrict`** mot clé est un mot clé contextuel. Les spécificateurs de restrictions, `cpu` et `amp`, ne sont pas des mots réservés. La liste des spécificateurs n'est pas extensible. Une fonction qui n’a pas de **`restrict`** clause est identique à une fonction qui possède la `restrict(cpu)` clause.

Une fonction qui possède la clause `restrict(amp)` présente les limitations suivantes :

- La fonction peut appeler uniquement des fonctions qui possèdent la clause `restrict(amp)`.

- La fonction doit être en mesure d'être inline.

- La fonction peut déclarer uniquement des variables,, **`int`** **`unsigned int`** **`float`** et **`double`** , ainsi que des classes et des structures qui contiennent uniquement ces types. **`bool`** est également autorisé, mais il doit être aligné sur 4 octets si vous l’utilisez dans un type composé.

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

  - **`goto`** publication.

  - instructions étiquetées,

  - **`try`****`catch`** instructions, ou **`throw`** .

  - Variables globales.

  - variables statiques Utilisez à la place le [mot clé tile_static](../cpp/tile-static-keyword.md) .

  - **`dynamic_cast`** casts.

  - **`typeid`** Opérateur.

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

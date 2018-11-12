---
title: Iterators
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: cf1f519521d86f2b7782fb93ed3b4aca4ecd5b24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643441"
---
# <a name="iterators"></a>Iterators

Un itérateur est un objet qui peut itérer sur les éléments dans un conteneur de bibliothèque standard C++ et fournir un accès à des éléments spécifiques. Les conteneurs de bibliothèque standard C++ fournissent tous des itérateurs permettant aux algorithmes d’accéder à leurs éléments de façon standard, sans avoir à se préoccuper du type de conteneur où les éléments sont stockés.

Vous pouvez utiliser des itérateurs explicitement à l’aide de membre et les fonctions globales telles que `begin()` et `end()` et opérateurs tels que **++** et **--** d’avancer ou vers l’arrière. Vous pouvez également utiliser des itérateurs implicitement avec une plage-boucle for ou (pour certains types d’itérateurs) l’opérateur d’indice  **\[]**.

Dans la bibliothèque standard C++, le début d’une séquence ou d’une plage est le premier élément. La fin d'une séquence ou d'une plage est toujours définie comme étant à l'emplacement suivant le dernier élément. Les fonctions globales `begin` et `end` retournent des itérateurs à un conteneur spécifié. La boucle d'itérateur explicite standard sur tous les éléments d'un conteneur ressemble à ceci :

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

La même chose peut être accomplie plus simplement avec une boucle for basée sur un intervalle :

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Il existe cinq catégories d'itérateurs. Par ordre de puissance croissante, les catégories sont :

- **Sortie**. Un *itérateur de sortie* `X` peut itérer vers l’avant sur une séquence à l’aide de la **++** opérateur et peut écrire un élément qu’une seule fois, à l’aide de la **&ast;** opérateur.

- **Entrée**. Un *itérateur d’entrée* `X` peut itérer vers l’avant sur une séquence à l’aide de la ++ (opérateur) et capable de lire un élément autant de fois à l’aide de la **&ast;** opérateur. Vous pouvez comparer des itérateurs d’entrée à l’aide de la **++** et **! =** opérateurs. Une fois que vous incrémentez une copie d'un itérateur d'entrée, aucune des autres copies ne peut être comparée, déréférencée ou incrémentée de façon fiable par la suite.

- **Vers l’avant**. Un *itérateur vers l’avant* `X` peut itérer vers l’avant sur une séquence avec le ++ opérateur et peut lire n’importe quel élément ou écrire des éléments non-const n’importe quel nombre de fois à l’aide de la **&ast;** opérateur. Vous pouvez accéder à des membres de l’élément à l’aide de la **->** opérateur et comparaison de transférer les itérateurs à l’aide de la **==** et **! =** opérateurs. Vous pouvez effectuer plusieurs copies d'un itérateur vers l'avant, chacune d'elles pouvant être déréférencée et incrémentée indépendamment. Itérateur vers l’avant qui est initialisé sans référence à n’importe quel conteneur est appelé un *itérateur vers l’avant null*. La comparaison d'itérateurs vers l'avant null donne toujours une égalité.

- **Bidirectionnel**. Un *itérateur bidirectionnel* `X` peut prendre la place d’un itérateur vers l’avant. Vous pouvez, toutefois, également décrémenter un itérateur bidirectionnel, comme dans `--X`, `X--`, ou `(V = *X--)`. Vous pouvez accéder aux membres de l'élément et comparer des itérateurs bidirectionnels de la même façon que pour des itérateurs vers l'avant.

- **Accès aléatoire**. Un *itérateur à accès aléatoire* `X` peut prendre la place d’un itérateur bidirectionnel. Avec un itérateur à accès aléatoire, vous pouvez utiliser l’opérateur d’indice  **\[]** pour accéder aux éléments. Vous pouvez utiliser la **+**, **-**, **+=** et **-=** opérateurs à déplacer avancer ou reculer un nombre spécifié d’éléments et pour calculer la distance entre les itérateurs. Vous pouvez comparer des itérateurs bidirectionnels à l’aide de **==**, **! =**, **\<**, **>**, **\< =**, et **>=**.

Tous les itérateurs peuvent être affectés ou copiés. Ils sont censés être des objets légers et sont souvent passés et retournés par valeur, et non par référence. Notez également qu'aucune des opérations décrites précédemment ne peut lever une exception lorsqu'elle est effectuée sur un itérateur valide.

La hiérarchie des catégories d'itérateur peut être résumée en indiquant trois séquences. Pour l'accès en écriture seule à une séquence, vous pouvez utiliser l'une des catégories suivantes :

> itérateur de sortie<br/>
> -> itérateur vers l’avant<br/>
> -> itérateur bidirectionnel<br/>
> -> itérateur à accès aléatoire<br/>

La flèche droite signifie "peut être remplacé par". Tout algorithme qui appelle un itérateur de sortie doit fonctionner correctement avec un itérateur vers l’avant, par exemple, mais *pas* dans l’autre sens.

Pour l'accès en lecture seule à une séquence, vous pouvez utiliser l'une des catégories suivantes :

> itérateur d’entrée<br/>
> -> itérateur vers l’avant<br/>
> -> itérateur bidirectionnel<br/>
> -> itérateur à accès aléatoire<br/>

Un itérateur d'entrée est le plus faible de toutes les catégories, dans ce cas.

Enfin, pour l'accès en lecture/écriture à une séquence, vous pouvez utiliser l'une des catégories suivantes :

> itérateur vers l’avant<br/>
> -> itérateur bidirectionnel<br/>
> -> itérateur à accès aléatoire<br/>

Un pointeur d'objet peut toujours servir d'itérateur à accès aléatoire, il peut donc être utilisé comme catégorie d'itérateur s'il prend en charge l'accès approprié en lecture et en écriture à la séquence qu'il désigne.

Un itérateur `Iterator` autre qu'un pointeur d'objet doit également définir les types de membres requis par la spécialisation `iterator_traits<Iterator>`. Notez que ces exigences peuvent être remplies en dérivant `Iterator` de la classe de base publique [iterator](../standard-library/iterator-struct.md).

Il est important de comprendre les promesses et les limites de chaque catégorie d’itérateur pour voir comment les itérateurs sont utilisés par les conteneurs et les algorithmes dans la bibliothèque standard C++.

> [!NOTE]
> Vous pouvez éviter d'utiliser des itérateurs explicitement avec des boucles for basées sur un intervalle. Pour plus d’informations, consultez [Range-based pour instruction](../cpp/range-based-for-statement-cpp.md).

Visual C++ propose désormais des itérateurs vérifiés et les itérateurs de débogage pour vous assurer que vous ne remplacez pas les limites de votre conteneur. Pour plus d’informations, consultez [itérateurs vérifiés](../standard-library/checked-iterators.md) et [Itérateurs de débogage, prise en charge](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

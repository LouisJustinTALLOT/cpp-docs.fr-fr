---
title: Conteneurs de la bibliothèque standard C++
ms.date: 11/04/2016
helpviewer_keywords:
- C++ Standard Library, template class containers
- containers, C++ Standard Library
ms.assetid: 8e915ca1-19ba-4f0d-93c8-e2c3bfd638eb
ms.openlocfilehash: a6f4da35468143e6d7c3dda684ed93f33e29b21d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412408"
---
# <a name="c-standard-library-containers"></a>Conteneurs de la bibliothèque standard C++

La Bibliothèque standard fournit divers conteneurs de type sécurisé pour stocker des collections d’objets connexes. Les conteneurs sont des modèles de classe. Quand vous déclarez une variable de conteneur, vous spécifiez le type des éléments que contiendra le conteneur. Vous pouvez construire des conteneurs avec des listes d'initialiseurs. Elles ont des fonctions membres pour ajouter et supprimer des éléments et exécuter d'autres opérations.

Les [itérateurs](../standard-library/iterators.md) vous permettent d’itérer les éléments dans un conteneur et d’accéder à chacun de ces éléments. Vous pouvez utiliser des itérateurs explicitement en utilisant les fonctions et les opérateurs de leurs membres, ainsi que des fonctions globales. Vous pouvez également les utiliser implicitement, par exemple avec une boucle for basée sur un intervalle. Les itérateurs pour tous les conteneurs de la bibliothèque standard C++ ont une interface commune, mais chaque conteneur définit ses propres itérateurs spécialisés.

Les conteneurs peuvent être divisés en trois catégories : les conteneurs de séquence, les conteneurs associatifs et les adaptateurs de conteneur.

## <a name="sequence_containers"></a> Conteneurs de séquence

Les conteneurs de séquence conservent l'ordonnancement des éléments insérés que vous spécifiez.

Un conteneur `vector` se comporte comme un tableau, mais il peut croître automatiquement selon les besoins. Il est en accès aléatoire et à stockage contigu, et sa longueur est hautement flexible. Pour ces raisons, entre autres, `vector` est le conteneur de séquence par défaut pour la plupart des applications. En cas de doute sur le type de conteneur de séquence à utiliser, commencez par utiliser un vecteur. Pour plus d’informations, consultez [vector, classe](../standard-library/vector-class.md).

Un conteneur `array` possède certains des avantages de `vector`, mais sa longueur n'est pas très flexible. Pour plus d’informations, consultez [array, classe](../standard-library/array-class-stl.md).

Un conteneur `deque` (file d'attente double) autorise les insertions et les suppressions rapides au début et à la fin du conteneur. Il partage les avantages offerts par l'accès aléatoire et la longueur flexible de `vector`, mais il n'est pas contigu. Pour plus d’informations, consultez [deque, classe](../standard-library/deque-class.md).

Un conteneur `list` est une liste à double liaison qui permet un accès bidirectionnel, des insertions rapides et des suppressions rapides n'importe où dans le conteneur, mais vous ne pouvez pas accéder de manière aléatoire à un élément du conteneur. Pour plus d’informations, consultez [list, classe](../standard-library/list-class.md).

Un conteneur `forward_list` est une liste à liaison unique, la version à accès direct de `list`. Pour plus d’informations, consultez [forward_list, classe](../standard-library/forward-list-class.md).

## <a name="associative-containers"></a>Conteneurs associatifs

Dans les conteneurs associatifs, les éléments sont insérés dans un ordre prédéfini, par exemple par ordre croissant. Des conteneurs associatifs non ordonnés sont également disponibles. Les conteneurs associatifs peuvent être regroupés dans deux sous-ensembles : les maps et les sets.

Un `map`, parfois appelé dictionnaire, se compose d'une paire clé/valeur. La clé est utilisée pour trier la séquence et la valeur est associée à cette clé. Par exemple, un `map` peut contenir des clés qui représentent chaque mot unique dans un texte et des valeurs correspondantes qui représentent le nombre de fois que chaque mot apparaît dans le texte. La version non ordonnée de `map` est `unordered_map`. Pour plus d’informations, consultez [map, classe](../standard-library/map-class.md) et [unordered_map, classe](../standard-library/unordered-map-class.md).

Un `set` est simplement un conteneur croissant d'éléments uniques. La valeur est également la clé. La version non ordonnée de `set` est `unordered_set`. Pour plus d’informations, consultez [set, classe](../standard-library/set-class.md) et [unordered_set, classe](../standard-library/unordered-set-class.md).

`map` et `set` autorisent l'insertion d'une seule instance d'une clé ou d'un élément dans le conteneur. Si plusieurs instances d'éléments sont nécessaires, utilisez `multimap` ou `multiset`. Les versions non ordonnées sont `unordered_multimap` et `unordered_multiset`. Pour plus d’informations, consultez [multimap, classe](../standard-library/multimap-class.md), [unordered_multimap, classe](../standard-library/unordered-multimap-class.md), [multiset, classe](../standard-library/multiset-class.md) et [unordered_multiset, classe](../standard-library/unordered-multiset-class.md).

Les maps et les sets ordonnés prennent en charge les itérateurs bidirectionnels et leurs équivalents non ordonnés prennent en charge les itérateurs vers l'avant. Pour plus d’informations, consultez [Itérateurs](../standard-library/iterators.md).

### <a name="heterogeneous-lookup-in-associative-containers-c14"></a>Recherche hétérogène dans les conteneurs associatifs (C++14)

Les conteneurs associatifs ordonnés (map, multimap, set et multiset) prennent désormais en charge la recherche hétérogène, ce qui signifie que vous n'êtes plus obligé de passer exactement le même type d'objet comme clé ou élément dans des fonctions membres comme `find()` et `lower_bound()`. Au lieu de cela, vous pouvez passer n'importe quel type pour lequel un `operator<` surchargé est défini et permet la comparaison avec le type de clé.

La recherche hétérogène est activée sur la base de l'abonnement quand vous spécifiez le comparateur « foncteur losange » `std::less<>` ou `std::greater<>` lors de la déclaration de la variable de conteneur, comme illustré ici :

```cpp
std::set<BigObject, std::less<>> myNewSet;
```

Si vous utilisez le comparateur par défaut, le conteneur se comporte exactement comme dans C++11 et versions antérieures.

L'exemple suivant montre comment surcharger `operator<` pour permettre aux utilisateurs d'un `std::set` d'effectuer des recherches simplement en passant une petite chaîne pouvant être comparée au membre `BigObject::id` de chaque objet.

```cpp
#include <set>
#include <string>
#include <iostream>
#include <functional>

using namespace std;

class BigObject
{
public:
    string id;
    explicit BigObject(const string& s) : id(s) {}
    bool operator< (const BigObject& other) const
    {
        return this->id < other.id;
    }

    // Other members....
};

inline bool operator<(const string& otherId, const BigObject& obj)
{
    return otherId < obj.id;
}

inline bool operator<(const BigObject& obj, const string& otherId)
{
    return obj.id < otherId;
}

int main()
{
    // Use C++14 brace-init syntax to invoke BigObject(string).
    // The s suffix invokes string ctor. It is a C++14 user-defined
    // literal defined in <string>
    BigObject b1{ "42F"s };
    BigObject b2{ "52F"s };
    BigObject b3{ "62F"s };
    set<BigObject, less<>> myNewSet; // C++14
    myNewSet.insert(b1);
    myNewSet.insert(b2);
    myNewSet.insert(b3);
    auto it = myNewSet.find(string("62F"));
    if (it != myNewSet.end())
        cout << "myNewSet element = " << it->id << endl;
    else
        cout << "element not found " << endl;

    // Keep console open in debug mode:
    cout << endl << "Press Enter to exit.";
    string s;
    getline(cin, s);
    return 0;
}

//Output: myNewSet element = 62F
```

Les fonctions membres suivantes dans map, multimap, set et multiset ont été surchargées pour prendre en charge la recherche hétérogène :

1. find

1. count

1. lower_bound

1. upper_bound

1. equal_range

## <a name="container-adapters"></a>Adaptateurs de conteneur

Un adaptateur de conteneur est une variante d'un conteneur de séquence ou associatif qui restreint l'interface à des fins de simplicité et de clarté. Les adaptateurs de conteneur ne prennent pas en charge les itérateurs.

Un conteneur `queue` suit la sémantique FIFO (premier entré, premier sorti). Le premier élément qui est *transféré par push* (autrement dit, qui est inséré dans la file d’attente) est le premier à être *dépilé* (autrement dit, à être supprimé de la file d’attente). Pour plus d’informations, consultez [queue, classe](../standard-library/queue-class.md).

Un conteneur `priority_queue` est organisé de telle façon que l'élément qui a la valeur la plus élevée soit toujours le premier dans la file d'attente. Pour plus d’informations, consultez [priority_queue, classe](../standard-library/priority-queue-class.md).

Un conteneur `stack` suit la sémantique LIFO (dernier entré, premier sorti). Le dernier élément inséré sur la pile est le premier élément dépilé. Pour plus d’informations, consultez [stack, classe](../standard-library/stack-class.md).

Les adaptateurs de conteneur ne peuvent pas être utilisés avec les algorithmes de la bibliothèque standard C++, car ils ne prennent pas en charge les itérateurs. Pour plus d’informations, consultez [Algorithmes](../standard-library/algorithms.md).

## <a name="requirements-for-container-elements"></a>Exigences pour les éléments de conteneurs

En général, s’ils peuvent être copiés, les éléments insérés dans un conteneur de la bibliothèque standard C++ peuvent être de presque n’importe quel type d’objet. Les éléments qui ne peuvent qu'être déplacés, par exemple ceux tel que `vector<unique_ptr<T>>` et qui sont créés à l'aide de `unique_ptr<>` fonctionnent tant que vous n'appelez pas de fonctions membres qui essaient de les copier.

Le destructeur n'est pas autorisé à lever une exception.

Les conteneurs associatifs ordonnés (décrits plus haut dans cet article) doivent avoir un opérateur de comparaison public défini. (Par défaut, l'opérateur est `operator<`, mais même les types qui ne fonctionnent pas avec `operator<` sont pris en charge.)

Certaines opérations sur les conteneurs peuvent également nécessiter un constructeur public par défaut et un opérateur d'équivalence public. Par exemple, les conteneurs associatifs non ordonnés nécessitent la prise en charge de l'égalité et du hachage.

## <a name="accessing-container-elements"></a>Accès aux éléments de conteneurs

Les éléments des conteneurs sont accessibles à l'aide d'itérateurs. Pour plus d'informations, consultez [Itérateurs](../standard-library/iterators.md).

> [!NOTE]
> Vous pouvez également utiliser des [boucles for basées sur une plage](../cpp/range-based-for-statement-cpp.md) pour itérer des collections de la bibliothèque standard C++.

## <a name="comparing-containers"></a>Comparaison des conteneurs

Tous les conteneurs surchargent l'opérateur == pour la comparaison de deux conteneurs du même type qui ont le même type d'élément. Vous pouvez utiliser == pour comparer un vector\<string> à un autre vector\<string>, mais vous ne pouvez pas l’utiliser pour comparer un vector\<string> à un list\<string> ou un vector\<string> à un vector\<char*>.  Dans C++98/03, vous pouvez utiliser [std::equal](algorithm-functions.md#equal) ou [std::mismatch](algorithm-functions.md#mismatch) pour comparer des types de conteneurs et/ou des types d’éléments différents. Dans C++11, vous pouvez également utiliser [std::is_permutation](algorithm-functions.md#is_permutation). Mais dans tous ces cas-là, les fonctions partent du principe que les conteneurs sont de même longueur. Si la deuxième plage est plus courte que la première, un comportement non défini se produit. Si la deuxième plage est plus longue, les résultats peuvent encore être incorrects, car la comparaison ne continue jamais au-delà de la fin de la première plage.

### <a name="comparing-dissimilar-containers-c14"></a>Comparaison de conteneurs différents (C++14)

Dans C ++ 14 et versions ultérieures, vous pouvez comparer des conteneurs et/ou des types d’éléments en utilisant l’une de le `std::equal`, `std::mismatch`, ou `std::is_permutation` surcharges qui acceptent deux plages complètes de fonctions. Ces surcharges vous permettent de comparer des conteneurs ayant des longueurs différentes. Elles sont beaucoup moins vulnérables aux erreurs des utilisateurs et sont optimisées pour retourner la valeur false en temps fixe quand des conteneurs de longueurs différentes sont comparés. C’est pourquoi nous vous recommandons d’utiliser ces surcharges sauf si (1) vous avez une raison très précise de ne pas le faire ou (2) vous utilisez un conteneur [std::list](../standard-library/list-class.md), qui ne tire pas profit des optimisations de double plage.

## <a name="see-also"></a>Voir aussi

[Conteneurs](../cpp/containers-modern-cpp.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<sample container>](../standard-library/sample-container.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>

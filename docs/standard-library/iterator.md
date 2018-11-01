---
title: '&lt;iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 1582f6167d8aae3a9d5a318726cc7404c7e1ea62
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640360"
---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;

Définit les primitives des itérateurs, les itérateurs prédéfinis et les itérateurs de flux, ainsi que plusieurs modèles de prise en charge. Les itérateurs prédéfinis incluent des adaptateurs d'insertion et d'inversion. Il existe trois classes d'adaptateurs d'itérateur d'insertion : avant, arrière et général. Ils fournissent une sémantique d'insertion, différente de la sémantique de remplacement que les itérateurs de fonctions membres de conteneurs fournissent.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iterator>

```

## <a name="remarks"></a>Notes

Les itérateurs sont une généralisation des pointeurs qui s’abstrait de leurs contraintes de telle sorte qu’un programme C++ puisse gérer différentes structures de données de manière uniforme. Les itérateurs se comportent comme des intermédiaires entre les conteneurs et les algorithmes génériques. Au lieu de traiter des types de données spécifiques, les algorithmes sont définis pour traiter une plage spécifiée par un type d'itérateur. Toute structure de données répondant aux exigences de l'itérateur peut être traitée par l'algorithme. Il existe cinq types ou catégories d'itérateur, chacun possédant son propre ensemble d'exigences et de fonctionnalités résultantes :

- De sortie : se déplace vers l'avant, peut stocker mais pas récupérer des valeurs, fourni par ostream et inserter.

- D'entrée : se déplace vers l'avant, peut récupérer mais pas stocker des valeurs, fourni par istream.

- D'avance : se déplace vers l'avant, peut stocker et récupérer des valeurs.

- Bidirectionnel : se déplace vers l'avant et l'arrière, peut stocker et récupérer des valeurs, fourni par list, set, multiset, map et multimap.

- D'accès aléatoire : éléments accessibles dans n'importe quel ordre, peut stocker et récupérer des valeurs, fourni par vector, deque, string et array.

Les itérateurs qui ont des exigences supérieures et disposent d'un accès plus performant aux éléments peuvent être utilisés à la place d'itérateurs ayant moins d'exigences. Par exemple, si un itérateur d'avance est appelé, alors un itérateur d'accès aléatoire peut être utilisé à la place.

Visual Studio ajoute des extensions aux itérateurs de la bibliothèque C++ standard pour prendre en charge diverses situations en mode débogage pour les itérateurs vérifiés et non vérifiés. Pour plus d’informations, consultez [Bibliothèques sécurisées : bibliothèque standard C++](../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[advance](../standard-library/iterator-functions.md#advance)|Incrémente un itérateur d'un nombre spécifié de positions.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Crée un itérateur qui peut insérer des éléments à la fin d'un conteneur spécifié.|
|[begin](../standard-library/iterator-functions.md#begin)|Récupère un itérateur sur le premier élément d'un conteneur spécifié.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Récupère un itérateur constant sur le premier élément d'un conteneur spécifié.|
|[cend](../standard-library/iterator-functions.md#cend)|Récupère un itérateur constant sur l'élément qui suit le dernier élément dans le conteneur spécifié.|
|[distance](../standard-library/iterator-functions.md#distance)|Détermine le nombre d'incréments entre les positions traitées par deux itérateurs.|
|[end](../standard-library/iterator-functions.md#end)|Récupère un itérateur de l'élément qui suit le dernier élément dans le conteneur spécifié.|
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Crée un itérateur qui peut insérer des éléments à l'avant d'un conteneur spécifié.|
|[inserter](../standard-library/iterator-functions.md#inserter)|Adaptateur d'itérateur qui ajoute un nouvel élément à un conteneur à un point d'insertion donné.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Crée un [checked_array_iterator](../standard-library/checked-array-iterator-class.md) qui peut être utilisé par d’autres algorithmes. **Remarque :** Cette fonction est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Retourne un itérateur de déplacement contenant l'itérateur fourni en tant qu'itérateur de base stocké.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Crée un [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) qui peut être utilisé par d’autres algorithmes. **Remarque :** Cette fonction est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.|
|[next](../standard-library/iterator-functions.md#next)|Itère un nombre de fois donné et retourne la nouvelle position de l'itérateur.|
|[prev](../standard-library/iterator-functions.md#prev)|Itère en sens inverse un nombre de fois donné et retourne la nouvelle position de l'itérateur.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[!=, opérateur](../standard-library/iterator-operators.md#op_neq)|Teste si l'objet itérateur situé à gauche de l'opérateur n'est pas égal à l'objet itérateur situé à droite.|
|[operator==](../standard-library/iterator-operators.md#op_eq_eq)|Teste si l'objet itérateur situé à gauche de l'opérateur est égal à l'objet itérateur situé à droite.|
|[operator<](../standard-library/iterator-operators.md#op_lt)|Teste si l'objet itérateur situé à gauche de l'opérateur est inférieur à l'objet itérateur situé à droite.|
|[operator\<=](../standard-library/iterator-operators.md#op_gt_eq)|Teste si l'objet itérateur situé à gauche de l'opérateur est inférieur ou égal à l'objet itérateur situé à droite.|
|[operator>](../standard-library/iterator-operators.md#op_gt)|Teste si l'objet itérateur situé à gauche de l'opérateur est supérieur à l'objet itérateur situé à droite.|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|Teste si l'objet itérateur situé à gauche de l'opérateur est supérieur ou égal à l'objet itérateur situé à droite.|
|[operator+](../standard-library/iterator-operators.md#op_add)|Ajoute un décalage à un itérateur et retourne le nouvel `reverse_iterator` qui se rapporte à l'élément inséré à la nouvelle position décalée.|
|[operator-](../standard-library/iterator-operators.md#operator-)|Soustrait un itérateur à un autre et retourne la différence.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|Cette classe de modèle décrit un objet itérateur de sortie. Elle insère des éléments dans un conteneur de type `Container`, auquel elle accède via l’élément protégé `pointer` objet qu’elle stocke appelé conteneur.|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Une classe qui fournit un type de retour pour une `iterator_category` fonction qui représente un itérateur bidirectionnel.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Classe qui accède à un tableau en utilisant un itérateur vérifié d'accès aléatoire. **Remarque :** Cette classe est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|Une classe qui fournit un type de retour pour une `iterator_category` fonction qui représente un itérateur vers l’avant.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|Cette classe de modèle décrit un objet itérateur de sortie. Elle insère des éléments dans un conteneur de type `Container`, auquel elle accède via l’élément protégé `pointer` objet qu’elle stocke appelé conteneur.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Une classe qui fournit un type de retour pour une `iterator_category` fonction qui représente un itérateur d’entrée.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|Cette classe de modèle décrit un objet itérateur de sortie. Elle insère des éléments dans un conteneur de type `Container`, auquel elle accède via l’élément protégé `pointer` objet qu’elle stocke appelé conteneur. Il stocke également l’élément protégé `iterator` objet, de la classe `Container::iterator`, appelée `iter`.|
|[istream_iterator](../standard-library/istream-iterator-class.md)|Cette classe de modèle décrit un objet itérateur d'entrée. Elle extrait des objets de classe `Ty` à partir d’un flux d’entrée, auquel elle accède via un objet qu’elle stocke, de type pointeur vers `basic_istream` \< **Elem**, **Tr**>.|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|Cette classe de modèle décrit un objet itérateur d'entrée. Elle insère des éléments de classe `Elem` dans un tampon de flux de sortie, auquel elle accède via un objet qu’elle stocke, de type `pointer` à `basic_streambuf` \< **Elem**, **Tr** >.|
|[iterator](../standard-library/iterator-struct.md)|Cette classe de modèle est utilisée comme type de base pour tous les itérateurs.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Classe d'assistance de modèle fournissant des types critiques qui sont associés à différents types d'itérateur afin de pouvoir être référencés de la même façon.|
|[move_iterator](../standard-library/move-iterator-class.md)|Un objet `move_iterator` stocke un itérateur d'accès aléatoire de type `RandomIterator`. Il se comporte comme un itérateur d'accès aléatoire, sauf lorsqu'il est déréférencé. Le résultat de `operator*` est implicitement casté en `value_type&&:` pour créer une `rvalue reference`.|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|Cette classe de modèle décrit un objet itérateur de sortie. Elle insère des objets de classe `Type` dans un flux de sortie, auquel elle accède via un objet qu’elle stocke, de type `pointer` à `basic_ostream` \< **Elem**, **Tr**>.|
|[ostreambuf_iterator, classe](../standard-library/ostreambuf-iterator-class.md)|Cette classe de modèle décrit un objet itérateur de sortie. Elle insère des éléments de classe `Elem` dans un tampon de flux de sortie, auquel elle accède via un objet qu’elle stocke, de type pointeur vers `basic_streambuf` \< **Elem**, **Tr**>.|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Une classe qui fournit un type de retour pour `iterator_category` (fonction) qui représente un itérateur de sortie.|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Une classe qui fournit un type de retour pour `iterator_category` fonction représentant un itérateur à accès aléatoire.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|Cette classe de modèle décrit un objet qui se comporte comme un itérateur d'accès aléatoire, mais en sens inverse.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Classe qui accède à un tableau en utilisant un itérateur non vérifié d'accès aléatoire. **Remarque :** Cette classe est une extension Microsoft de la bibliothèque standard C++. Le code implémenté à l’aide de cette fonction ne peut pas être utilisé dans les environnements de build C++ standard qui ne prennent pas en charge cette extension Microsoft.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>

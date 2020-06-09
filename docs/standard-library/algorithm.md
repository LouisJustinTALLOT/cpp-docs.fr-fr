---
title: '&lt;algorithm&gt;'
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: d36ee5ea0d38455b52cb988dc30b13d47be16e53
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623847"
---
# <a name="ltalgorithmgt"></a>&lt;algorithm&gt;

Définit les fonctions de modèle du conteneur de bibliothèque C++ Standard qui exécutent des algorithmes.

## <a name="syntax"></a>Syntaxe

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> La \<algorithm> bibliothèque utilise également l' `#include <initializer_list>` instruction.

## <a name="remarks"></a>Notes

Les algorithmes de la bibliothèque C++ Standard sont génériques, car ils peuvent traiter diverses structures de données. Les structures de données qu’ils peuvent traiter incluent non seulement les classes de conteneur de bibliothèque C++ Standard, comme `vector` et `list`, mais aussi les structures de données définies par programmation et les tableaux d’éléments qui répondent aux exigences d’un algorithme en particulier. Ces algorithmes de la bibliothèque C++ Standard atteignent ce niveau de généralité en parcourant les éléments d’un conteneur indirectement via des itérateurs.

Les algorithmes de la bibliothèque C++ Standard traitent des plages d’itérateurs qui sont généralement spécifiées par leur position de début ou de fin. Les plages référencées doivent être valides, c'est-à-dire que tous les pointeurs de ces plages doivent pouvoir être déréférencés et, que dans les séquences de chaque plage, la dernière position doit être accessible depuis la première par incrémentation.

Les algorithmes de la bibliothèque C++ Standard étendent les actions prises en charge par les opérations et les fonctions membres de chaque conteneur de bibliothèque C++ Standard, et permettent, entre autres choses, l’utilisation simultanée de plusieurs types d’objets de conteneur. Deux suffixes ont été utilisés pour transmettre des informations concernant l'usage des algorithmes.

- Le `_if` suffixe indique que l’algorithme est utilisé avec des objets de fonction opérant sur les valeurs des éléments plutôt que sur les éléments eux-mêmes. L'algorithme `find_if` recherche les éléments dont les valeurs répondent au critère spécifié par un objet de fonction, et l'algorithme `find` recherche une valeur particulière.

- Le suffixe _copy indique que l'algorithme manipule les valeurs des éléments, mais copie également les valeurs modifiées dans une plage de destination. L'algorithme `reverse` inverse l'ordre des éléments d'une plage, et l'algorithme `reverse_copy` copie également le résultat dans une plage de destination.

Les algorithmes de la bibliothèque C++ Standard sont souvent classés par groupes selon leur usage ou leurs exigences. Il s'agit notamment des algorithmes de modification qui changent la valeur des éléments, contrairement aux autres algorithmes. Les algorithmes de mutation modifient l'ordre des éléments, mais pas leurs valeurs. Les algorithmes de suppression peuvent éliminer les éléments d'une plage ou d'une copie d'une plage. Les algorithmes de tri réorganisent les éléments d’une plage de différentes façons et les algorithmes de plages triées agissent uniquement sur les plages dont les éléments ont été triés d’une manière particulière.

Les algorithmes numériques de la bibliothèque standard C++ fournis pour le traitement numérique possèdent leur propre fichier d’en-tête [\<numeric>](numeric.md) , et les objets de fonction et les adaptateurs sont définis dans l’en-tête [\<functional>](functional.md) . les objets de fonction qui retournent des valeurs booléennes sont appelés prédicats. Le prédicat binaire par défaut est le `operator<` de comparaison. En général, les éléments qui sont triés ne doivent pas être équivalents, afin que, avec deux éléments quelconques donnés, il soit possible de déterminer qu'ils sont équivalents (dans le sens où l'un n'est pas inférieur à l'autre) ou que l'un est inférieur à l'autre. Cela entraîne un tri des éléments non équivalents.

### <a name="function-templates"></a>Modèles de fonctions

|||
|-|-|
|[adjacent_find](algorithm-functions.md#adjacent_find)|Recherche deux éléments adjacents qui ont la même valeur ou qui répondent à une condition spécifiée.|
|[all_of](algorithm-functions.md#all_of)|Retourne la **valeur true** lorsqu’une condition est présente à chaque élément d’une plage donnée.|
|[any_of](algorithm-functions.md#any_of)|Retourne la **valeur true** lorsqu’une condition est présente au moins une fois dans la plage d’éléments spécifiée.|
|[binary_search](algorithm-functions.md#binary_search)|Teste si un élément d’une plage triée est égal à une valeur spécifiée ou équivalent, selon une condition spécifiée par un prédicat binaire.|
|[bride](algorithm-functions.md#clamp)||
|[copy](algorithm-functions.md#copy)|Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions, du haut vers le bas.|
|[copy_backward](algorithm-functions.md#copy_backward)|Assigne les valeurs des éléments d'une plage source à une plage de destination, en procédant à une itération via la séquence source d'éléments et en leur assignant de nouvelles positions vers le haut.|
|[copy_if](algorithm-functions.md#copy_if)|Copier tous les éléments d’une plage donnée qui testent la **valeur true** pour une condition spécifiée|
|[copy_n](algorithm-functions.md#copy_n)|Copie un nombre spécifié d'éléments.|
|[count](algorithm-functions.md#count)|Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.|
|[count_if](algorithm-functions.md#count_if)|Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une condition spécifiée.|
|[valeur](algorithm-functions.md#equal)|Compare deux plages, élément par élément, à la recherche d’une égalité ou d’une équivalence, selon une condition spécifiée par un prédicat binaire.|
|[equal_range](algorithm-functions.md#equal_range)|Recherche une paire de positions dans une plage triée. La première inférieure ou équivalente à la position d’un élément spécifié, et la deuxième supérieure à la position de cet élément. L’équivalence ou le tri utilisés pour établir des positions dans la séquence peuvent être spécifiés par un prédicat binaire.|
|[complète](algorithm-functions.md#fill)|Affecte la même nouvelle valeur à chaque élément d'une plage spécifiée.|
|[fill_n](algorithm-functions.md#fill_n)|Assigne une nouvelle valeur à un nombre spécifié d'éléments d'une plage qui commence par un élément particulier.|
|[find](algorithm-functions.md#find)|Recherche la position de la première occurrence d'un élément d'une plage ayant une valeur spécifiée.|
|[find_end](algorithm-functions.md#find_end)|Recherche dans une plage la dernière sous-séquence qui est identique à une séquence spécifiée ou qui est équivalente, selon une condition spécifiée par un prédicat binaire.|
|[find_first_of](algorithm-functions.md#find_first_of)|Recherche la première occurrence parmi plusieurs valeurs d’une plage cible, ou la première occurrence parmi plusieurs éléments qui sont équivalents, selon une condition spécifiée par un prédicat binaire, à un ensemble d’éléments spécifiés.|
|[find_if](algorithm-functions.md#find_if)|Recherche la position de la première occurrence d'un élément d'une plage qui répond à une condition spécifiée.|
|[find_if_not](algorithm-functions.md#find_if_not)|Retourne le premier élément d'une plage spécifiée qui ne répond pas à une condition.|
|[for_each](algorithm-functions.md#for_each)|Applique un objet de fonction spécifié à chaque élément d'une plage, du haut vers le bas, et retourne l'objet de la fonction.|
|[for_each_n](algorithm-functions.md#for_each_n)||
|[automatiquement](algorithm-functions.md#generate)|Assigne les valeurs générées par un objet de fonction à chaque élément d'une plage.|
|[generate_n](algorithm-functions.md#generate_n)|Assigne les valeurs générées par un objet de fonction à un nombre spécifié d'éléments d'une plage, et retourne à la position située juste après la dernière valeur assignée.|
|[offre](algorithm-functions.md#includes)|Teste si une plage triée contient tous les éléments d’une autre plage triée. Le critère de tri ou d’équivalence entre les éléments peut être spécifié par un prédicat binaire.|
|[inplace_merge](algorithm-functions.md#inplace_merge)|Regroupe les éléments de deux plages triées consécutives au sein d’une même plage triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[is_heap](algorithm-functions.md#is_heap)|Retourne la **valeur true** si les éléments de la plage spécifiée forment un segment de mémoire.|
|[is_heap_until](algorithm-functions.md#is_heap_until)|Retourne la **valeur true** si la plage spécifiée forme un tas jusqu’au dernier élément.|
|[is_partitioned](algorithm-functions.md#is_partitioned)|Retourne la **valeur true** si tous les éléments d’une plage donnée qui testent la **valeur true** pour une condition précèdent tous les éléments qui testent **false**.|
|[is_permutation](algorithm-functions.md#is_permutation)|Détermine si les éléments d'une plage donnée forment une permutation valide.|
|[is_sorted](algorithm-functions.md#is_sorted)|Retourne la **valeur true** si les éléments de la plage spécifiée sont triés.|
|[is_sorted_until](algorithm-functions.md#is_sorted_until)|Retourne la **valeur true** si les éléments de la plage spécifiée sont triés.|
|[iter_swap](algorithm-functions.md#iter_swap)|Échange deux valeurs référencées par une paire d'itérateurs spécifiés.|
|[lexicographical_compare](algorithm-functions.md#lexicographical_compare)|Compare deux séquences, élément par élément, pour déterminer lequel est inférieur à l'autre.|
|[lower_bound](algorithm-functions.md#lower_bound)|Recherche la position du premier élément d’une plage triée dont la valeur est supérieure ou équivalente à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[make_heap](algorithm-functions.md#make_heap)|Convertit les éléments d’une plage spécifiée en un tas, dans lequel le premier élément est le plus grand, et pour lequel un critère de tri peut être spécifié à l’aide d’un prédicat binaire.|
|[max](algorithm-functions.md#max)|Compare deux objets et retourne le plus grand des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.|
|[max_element](algorithm-functions.md#max_element)|Recherche la première occurrence du plus grand élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.|
|[fusion](algorithm-functions.md#merge)|Regroupe tous les éléments de deux plages sources triées au sein d’une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[min](algorithm-functions.md#min)|Compare deux objets et retourne le plus petit des deux. Un critère de tri peut être spécifié à l’aide d’un prédicat binaire.|
|[min_element](algorithm-functions.md#min_element)|Recherche la première occurrence du plus petit élément dans une plage spécifiée. Un critère de tri peut être spécifié par un prédicat binaire.|
|[MinMax](algorithm-functions.md#minmax)|Compare deux paramètres d'entrée et les retourne en tant que paire, du plus petit au plus grand.|
|[minmax_element](algorithm-functions.md#minmax_element)|Exécute le travail effectué par [min_element](algorithm-functions.md#min_element) et [max_element](algorithm-functions.md#max_element) au sein d’un même appel.|
|[Concorde](algorithm-functions.md#mismatch)|Compare deux plages, élément par élément, à la recherche d’une égalité ou d’une équivalence, selon une condition spécifiée par un prédicat binaire, et recherche la première position où se trouve une différence.|
|[&lt;&gt;déplacement ALG](algorithm-functions.md#alg_move)|Déplace les éléments associés à une plage spécifiée.|
|[move_backward](algorithm-functions.md#move_backward)|Déplace les éléments d'un itérateur vers un autre. Le déplacement commence par le dernier élément d'une plage spécifiée, et se termine par le premier élément de cette plage.|
|[next_permutation](algorithm-functions.md#next_permutation)|Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.|
|[none_of](algorithm-functions.md#none_of)|Retourne la **valeur true** lorsqu’une condition n’est jamais présente parmi les éléments de la plage donnée.|
|[nth_element](algorithm-functions.md#nth_element)|Partitionne une plage d’éléments, en localisant correctement le *n*ième élément de la séquence dans la plage, de sorte que tous les éléments qui le précèdent sont inférieurs ou égaux et que tous les éléments qui le suivent dans la séquence soient supérieurs ou égaux.|
|[partial_sort](algorithm-functions.md#partial_sort)|Réorganise un nombre spécifié d’éléments plus petits au sein d’une plage, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.|
|[partial_sort_copy](algorithm-functions.md#partial_sort_copy)|Copie les éléments d’une plage source dans une plage de destination. Les éléments sources sont triés par ordre croissant ou selon un autre prédicat binaire spécifié.|
|[non](algorithm-functions.md#partition)|Répartit les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas.|
|[partition_copy](algorithm-functions.md#partition_copy)|Copie les éléments pour lesquels une condition a la **valeur true** pour une destination, et pour laquelle la condition est **false** à une autre. Les éléments doivent provenir d'une plage spécifiée.|
|[partition_point](algorithm-functions.md#partition_point)|Retourne le premier élément d'une plage donnée qui ne répond pas à une condition. Les éléments sont triés de sorte que ceux qui répondent à la condition précèdent ceux qui n'y répondent pas.|
|[pop_heap](algorithm-functions.md#pop_heap)|Retire le plus grand élément du début du tas et le place à l'avant-dernière position de la plage, puis forme un nouveau tas à partir des éléments restants.|
|[prev_permutation](algorithm-functions.md#prev_permutation)|Réorganise les éléments d’une plage, de sorte que le tri d’origine soit remplacé par la prochaine permutation plus élevée d’un point de vue lexicographique (s’il en existe une). La notion de "prochaine" peut être définie à l’aide d’un prédicat binaire.|
|[push_heap](algorithm-functions.md#push_heap)|Ajoute un élément qui se trouve à la fin d'une plage à un tas existant, constitué des éléments précédents de la plage.|
|[random_shuffle](algorithm-functions.md#random_shuffle)|Réorganise une séquence de *N* éléments d’une plage en une séquence de *N*! dispositions possibles, sélectionnées de manière aléatoire.|
|[remove](algorithm-functions.md#remove)|Élimine une valeur spécifiée d'une plage donnée sans modifier l'ordre des éléments restants, et retourne la fin d'une nouvelle plage exempte de la valeur spécifiée.|
|[remove_copy](algorithm-functions.md#remove_copy)|Copie les éléments d'une plage source vers une plage de destination. Les éléments ayant une valeur spécifiée ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.|
|[remove_copy_if](algorithm-functions.md#remove_copy_if)|Copie les éléments d'une plage source vers une plage de destination. Les éléments répondant à un prédicat ne sont pas copiés. L'ordre des éléments restants n'est pas modifié et la fin d'une nouvelle plage de destination est retournée.|
|[remove_if](algorithm-functions.md#remove_if)|Élimine d’une plage donnée les éléments qui répondent à un prédicat, sans modifier l’ordre des éléments restants et en retournant la fin d’une nouvelle plage exempte de la valeur spécifiée.|
|[replace](algorithm-functions.md#replace)|Examine tous les éléments d'une plage et les remplace s'ils correspondent à une valeur spécifiée.|
|[replace_copy](algorithm-functions.md#replace_copy)|Examine tous les éléments d'une plage source et les remplace s'ils correspondent à une valeur spécifiée, tout en copiant le résultat dans une nouvelle plage de destination.|
|[replace_copy_if](algorithm-functions.md#replace_copy_if)|Examine tous les éléments d'une plage source et les remplace s'ils répondent à un prédicat, tout en copiant le résultat dans une nouvelle plage de destination.|
|[replace_if](algorithm-functions.md#replace_if)|Examine tous les éléments d’une plage et les remplace s’ils répondent à un prédicat spécifié.|
|[TVA](algorithm-functions.md#reverse)|Inverse l'ordre des éléments d'une plage.|
|[reverse_copy](algorithm-functions.md#reverse_copy)|Inverse l'ordre des éléments d'une plage source, tout en les copiant dans une plage de destination.|
|[MUTE](algorithm-functions.md#rotate)|Échange les éléments de deux plages adjacentes.|
|[rotate_copy](algorithm-functions.md#rotate_copy)|Échange les éléments de deux plages adjacentes au sein d'une plage source et copie le résultat dans une plage de destination.|
|[exemple](algorithm-functions.md#sample)||
|[search](algorithm-functions.md#search)|Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.|
|[search_n](algorithm-functions.md#search_n)|Recherche la première sous-séquence d’une plage dont un nombre spécifié d’éléments ont une valeur particulière ou une relation à cette valeur, selon un prédicat binaire spécifié.|
|[set_difference](algorithm-functions.md#set_difference)|Regroupe tous les éléments qui appartiennent à une plage source triée, mais pas à une autre plage source triée, en une même plage de destination triée. Un critère de tri peut être spécifié par un prédicat binaire.|
|[set_intersection](algorithm-functions.md#set_intersection)|Regroupe tous les éléments de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[set_symmetric_difference](algorithm-functions.md#set_symmetric_difference)|Regroupe tous les éléments qui appartiennent à l'une de deux plages sources triées (mais pas aux deux) au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[set_union](algorithm-functions.md#set_union)|Regroupe tous les éléments qui appartiennent au moins à l'une de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|
|[sort](algorithm-functions.md#sort)|Réorganise les éléments d’une plage spécifiée, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.|
|[lecture aléatoire](algorithm-functions.md#shuffle)|Lit de façon aléatoire (réorganise) les éléments pour une plage donnée à l'aide d'un générateur de nombres aléatoires.|
|[sort_heap](algorithm-functions.md#sort_heap)|Convertit un tas en une plage triée.|
|[stable_partition](algorithm-functions.md#stable_partition)|Classe les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas, et l’ordre relatif des éléments équivalents doit être conservé.|
|[stable_sort](algorithm-functions.md#stable_sort)|Classe les éléments d’une plage spécifiée dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire, et conserve l’ordre relatif des éléments équivalents.|
|[swap](algorithm-functions.md#swap)|Échange les valeurs des éléments de deux types d'objets, en assignant le contenu du premier objet au deuxième objet, et le contenu du deuxième au premier.|
|[swap_ranges](algorithm-functions.md#swap_ranges)|Échange les éléments d'une plage avec ceux d'une autre plage de taille égale.|
|[transform](algorithm-functions.md#transform)|Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination.|
|[unique](algorithm-functions.md#unique)|Supprime les éléments en double adjacents dans une plage spécifiée.|
|[unique_copy](algorithm-functions.md#unique_copy)|Copie les éléments d'une plage source dans une plage de destination, à l'exception des éléments en double adjacents.|
|[upper_bound](algorithm-functions.md#upper_bound)|Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](cpp-standard-library-reference.md)

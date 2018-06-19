---
title: algorithme (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 30e347905c6802e544cb9f81c045f9cc881f29fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111326"
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
Définit les fonctions de modèle de conteneur STL/CLR qui exécutent des algorithmes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <cliext/algorithm>  
```  
  
## <a name="functions"></a>Fonctions  
  
|Fonction|Description|  
|--------------|-----------------|  
|[adjacent_find (STL/CLR)](../dotnet/adjacent-find-stl-clr.md)|Recherche deux éléments adjacents qui sont égaux.|  
|[binary_search (STL/CLR)](../dotnet/binary-search-stl-clr.md)|Teste si une séquence triée contient une valeur donnée.|  
|[copy (STL/CLR)](../dotnet/copy-stl-clr.md)|Copie les valeurs d’une plage source à une plage de destination, une itération dans la direction vers l’avant.|  
|[copy_backward (STL/CLR)](../dotnet/copy-backward-stl-clr.md)|Copie les valeurs d’une plage source à une plage de destination, une itération dans la direction descendante.|  
|[count (STL/CLR)](../dotnet/count-stl-clr.md)|Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une valeur spécifiée.|  
|[count_if (STL/CLR)](../dotnet/count-if-stl-clr.md)|Retourne le nombre d'éléments d'une plage dont les valeurs correspondent à une condition spécifiée.|  
|[equal (STL/CLR)](../dotnet/equal-stl-clr.md)|Compare deux plages, élément par élément.|  
|[equal_range (STL/CLR)](../dotnet/equal-range-stl-clr.md)|Recherche d’une séquence ordonnée de valeurs et retourne des deux positions qui délimitent une sous-séquence des valeurs qui sont toutes égales à un élément donné.|  
|[fill (STL/CLR)](../dotnet/fill-stl-clr.md)|Affecte la même nouvelle valeur à chaque élément d'une plage spécifiée.|  
|[fill_n (STL/CLR)](../dotnet/fill-n-stl-clr.md)|Attribue une nouvelle valeur à un nombre spécifié d’éléments d’une plage commençant par un élément particulier.|  
|[find (STL/CLR)](../dotnet/find-stl-clr.md)|Retourne la position de la première occurrence d’une valeur spécifiée.|  
|[find_end (STL/CLR)](../dotnet/find-end-stl-clr.md)|Retourne la dernière sous-séquence d’une plage qui est identique à une séquence spécifiée.|  
|[find_first_of (STL/CLR)](../dotnet/find-first-of-stl-clr.md)|Recherche une plage pour la première occurrence de l’un d’une plage d’éléments.|  
|[find_if (STL/CLR)](../dotnet/find-if-stl-clr.md)|Retourne la position du premier élément dans une séquence de valeurs, où l’élément satisfait à une condition spécifiée.|  
|[for_each (STL/CLR)](../dotnet/for-each-stl-clr.md)|Applique un objet de fonction spécifiée à chaque élément dans une séquence de valeurs et retourne l’objet de fonction.|  
|[generate (STL/CLR)](../dotnet/generate-stl-clr.md)|Assigne les valeurs générées par un objet de fonction à chaque élément d’une séquence de valeurs.|  
|[generate_n (STL/CLR)](../dotnet/generate-n-stl-clr.md)|Assigne les valeurs générées par un objet de fonction à un nombre spécifié d’éléments.|  
|[includes (STL/CLR)](../dotnet/includes-stl-clr.md)|Teste si une plage triée contient tous les éléments dans une autre plage triée.|  
|[inplace_merge (STL/CLR)](../dotnet/inplace-merge-stl-clr.md)|Regroupe les éléments de deux plages triées consécutives dans une même plage triée.|  
|[iter_swap (STL/CLR)](../dotnet/iter-swap-stl-clr.md)|Échange deux valeurs référencées par une paire d'itérateurs spécifiés.|  
|[lexicographical_compare (STL/CLR)](../dotnet/lexicographical-compare-stl-clr.md)|Compare deux séquences, élément par élément, identifiant la séquence qui est le plus petit des deux.|  
|[lower_bound (STL/CLR)](../dotnet/lower-bound-stl-clr.md)|Recherche la position du premier élément d’une séquence ordonnée de valeurs qui a une valeur supérieure ou égale à une valeur spécifiée.|  
|[make_heap (STL/CLR)](../dotnet/make-heap-stl-clr.md)|Convertit les éléments d’une plage spécifiée en un tas, où le premier élément sur le tas est le plus grand.|  
|[max (STL/CLR)](../dotnet/max-stl-clr.md)|Compare deux objets et retourne la plus grande des deux.|  
|[max_element (STL/CLR)](../dotnet/max-element-stl-clr.md)|Recherche le plus grand élément dans une séquence spécifique de valeurs.|  
|[merge (STL/CLR)](../dotnet/merge-stl-clr.md)|Combine tous les éléments de deux plages sources triées dans une plage de destination triée unique.|  
|[min (STL/CLR)](../dotnet/min-stl-clr.md)|Compare deux objets et retourne le plus petit des deux.|  
|[min_element (STL/CLR)](../dotnet/min-element-stl-clr.md)|Recherche le plus petit élément dans une séquence spécifique de valeurs.|  
|[mismatch (STL/CLR)](../dotnet/mismatch-stl-clr.md)|Compare deux plages, élément par élément et retourne la première position où se trouve une différence.|  
|[next_permutation (STL/CLR)](../dotnet/next-permutation-stl-clr.md)|Réorganise les éléments dans une plage de sorte que le tri d’origine est remplacé par la permutation supérieure lexicographique suivante si elle existe.|  
|[nth_element (STL/CLR)](../dotnet/nth-element-stl-clr.md)|Partitionne une séquence d’éléments, en recherchant le `n`ième élément de la séquence de sorte que tous les éléments le précédant lui soient inférieur ou égal à celui-ci et tous les éléments qui suivent sont supérieurs ou égaux.|  
|[partial_sort (STL/CLR)](../dotnet/partial-sort-stl-clr.md)|Réorganise un nombre spécifié d’éléments plus petits dans une plage dans un ordre non décroissant.|  
|[partial_sort_copy (STL/CLR)](../dotnet/partial-sort-copy-stl-clr.md)|Copie les éléments d’une plage source dans une plage de destination telles que les éléments de la plage source sont classés.|  
|[partition (STL/CLR)](../dotnet/partition-stl-clr.md)|Réorganise les éléments dans une plage de telle sorte que les éléments qui répondent à un prédicat unaire précèdent ceux qui ne répondent pas.|  
|[pop_heap (STL/CLR)](../dotnet/pop-heap-stl-clr.md)|Déplace le plus grand élément du début d’un segment de mémoire à la fin, puis forme un nouveau tas à partir des éléments restants.|  
|[prev_permutation (STL/CLR)](../dotnet/prev-permutation-stl-clr.md)|Réorganise une séquence d’éléments afin que le tri d’origine est remplacé par la permutation supérieure lexicographique précédente si elle existe.|  
|[push_heap (STL/CLR)](../dotnet/push-heap-stl-clr.md)|Ajoute un élément qui se trouve à la fin d'une plage à un tas existant, constitué des éléments précédents de la plage.|  
|[random_shuffle (STL/CLR)](../dotnet/random-shuffle-stl-clr.md)|Réorganise une séquence de `N` éléments d’une plage dans une des `N`! dispositions possibles, sélectionnées de manière aléatoire.|  
|[remove (STL/CLR)](../dotnet/remove-stl-clr.md)|Supprime une valeur spécifiée à partir d’une plage donnée sans porter atteinte à l’ordre des éléments restants et retourne la fin d’une nouvelle plage de la valeur spécifiée.|  
|[remove_copy (STL/CLR)](../dotnet/remove-copy-stl-clr.md)|Copie les éléments d’une plage source dans une plage de destination, à ceci près que les éléments d’une valeur spécifiée ne sont pas copiés, sans porter atteinte à l’ordre des éléments restants.|  
|[remove_copy_if (STL/CLR)](../dotnet/remove-copy-if-stl-clr.md)|Copie les éléments d’une plage source vers une plage de destination, à l’exception de celles qui répondent à un prédicat, sans porter atteinte à l’ordre des éléments restants.|  
|[remove_if (STL/CLR)](../dotnet/remove-if-stl-clr.md)|Supprime les éléments qui répondent à un prédicat d’une plage donnée sans porter atteinte à l’ordre des éléments restants. .|  
|[replace (STL/CLR)](../dotnet/replace-stl-clr.md)|Remplace les éléments d’une plage qui correspond à une valeur spécifiée avec une nouvelle valeur.|  
|[replace_copy (STL/CLR)](../dotnet/replace-copy-stl-clr.md)|Copie les éléments d’une plage source vers une plage de destination, en remplaçant les éléments qui correspondent à une valeur spécifiée avec une nouvelle valeur.|  
|[replace_copy_if (STL/CLR)](../dotnet/replace-copy-if-stl-clr.md)|Examine tous les éléments d'une plage source et les remplace s'ils répondent à un prédicat, tout en copiant le résultat dans une nouvelle plage de destination.|  
|[replace_if (STL/CLR)](../dotnet/replace-if-stl-clr.md)|Examine tous les éléments d’une plage et les remplace s’ils répondent à un prédicat spécifié.|  
|[reverse (STL/CLR)](../dotnet/reverse-stl-clr.md)|Inverse l'ordre des éléments d'une plage.|  
|[reverse_copy (STL/CLR)](../dotnet/reverse-copy-stl-clr.md)|Inverse l’ordre des éléments d’une plage source tout en les copiant dans une plage de destination.|  
|[rotate (STL/CLR)](../dotnet/rotate-stl-clr.md)|Échange les éléments de deux plages adjacentes.|  
|[rotate_copy (STL/CLR)](../dotnet/rotate-copy-stl-clr.md)|Échange les éléments de deux plages adjacentes au sein d'une plage source et copie le résultat dans une plage de destination.|  
|[search (STL/CLR)](../dotnet/search-stl-clr.md)|Recherche la première occurrence d’une séquence au sein d’une plage cible dont les éléments sont égaux à ceux d’une séquence d’éléments donnée ou dont les éléments sont équivalents à ceux d’une séquence donnée, selon un prédicat binaire spécifié.|  
|[search_n (STL/CLR)](../dotnet/search-n-stl-clr.md)|Recherche la première sous-séquence d’une plage dont un nombre spécifié d’éléments ont une valeur particulière ou une relation à cette valeur, selon un prédicat binaire spécifié.|  
|[set_difference (STL/CLR)](../dotnet/set-difference-stl-clr.md)|Regroupe tous les éléments qui appartiennent à une plage source triée, mais pas à une autre plage source triée, en une même plage de destination triée. Un critère de tri peut être spécifié par un prédicat binaire.|  
|[set_intersection (STL/CLR)](../dotnet/set-intersection-stl-clr.md)|Regroupe tous les éléments de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|  
|[set_symmetric_difference (STL/CLR)](../dotnet/set-symmetric-difference-stl-clr.md)|Regroupe tous les éléments qui appartiennent à l'une de deux plages sources triées (mais pas aux deux) au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|  
|[set_union (STL/CLR)](../dotnet/set-union-stl-clr.md)|Regroupe tous les éléments qui appartiennent au moins à l'une de deux plages sources triées au sein d'une même plage de destination triée. Le critère de tri peut être spécifié par un prédicat binaire.|  
|[sort (STL/CLR)](../dotnet/sort-stl-clr.md)|Réorganise les éléments d’une plage spécifiée, dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire.|  
|[sort_heap (STL/CLR)](../dotnet/sort-heap-stl-clr.md)|Convertit un tas en une plage triée.|  
|[stable_partition (STL/CLR)](../dotnet/stable-partition-stl-clr.md)|Classe les éléments d’une plage en deux ensembles disjoints. Les éléments qui répondent à un prédicat unaire doivent précéder ceux qui n’y répondent pas, et l’ordre relatif des éléments équivalents doit être conservé.|  
|[stable_sort (STL/CLR)](../dotnet/stable-sort-stl-clr.md)|Classe les éléments d’une plage spécifiée dans un ordre non décroissant, ou selon un critère de tri spécifié par un prédicat binaire, et conserve l’ordre relatif des éléments équivalents.|  
|[swap (STL/CLR)](../dotnet/swap-stl-clr.md)|Échange les valeurs des éléments de deux types d'objets, en assignant le contenu du premier objet au deuxième objet, et le contenu du deuxième au premier.|  
|[swap_ranges (STL/CLR)](../dotnet/swap-ranges-stl-clr.md)|Échange les éléments d'une plage avec ceux d'une autre plage de taille égale.|  
|[transform (STL/CLR)](../dotnet/transform-stl-clr.md)|Applique un objet de fonction spécifié à chaque élément d'une plage source ou à une paire d'éléments de deux plages sources, et copie les valeurs de retour de l'objet de fonction dans une plage de destination.|  
|[unique (STL/CLR)](../dotnet/unique-stl-clr.md)|Supprime les éléments en double adjacents dans une plage spécifiée.|  
|[unique_copy (STL/CLR)](../dotnet/unique-copy-stl-clr.md)|Copie les éléments d'une plage source dans une plage de destination, à l'exception des éléments en double adjacents.|  
|[upper_bound (STL/CLR)](../dotnet/upper-bound-stl-clr.md)|Recherche la position du premier élément d’une plage triée dont la valeur est supérieure à une valeur spécifiée. Le critère de tri peut être spécifié par un prédicat binaire.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/algorithme >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
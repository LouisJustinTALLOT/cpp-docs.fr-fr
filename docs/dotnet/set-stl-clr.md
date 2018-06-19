---
title: définir (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- set class [STL/CLR]
ms.assetid: 27d3628c-741a-43a7-bef1-5085536f679e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d6a7ebf4d15d85cb43a6f7101c70e444067a3f7b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172801"
---
# <a name="set-stlclr"></a>set (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès bidirectionnel. Vous utilisez le conteneur `set` pour gérer une séquence d’éléments sous forme d’arborescence triée à charge équilibrée (presque) des nœuds, chacun stocker un élément.  
  
 Dans la description ci-dessous, `GValue` est identique à `GKey`, qui à son tour est le même que `Key` , sauf si ce dernier est un type référence, auquel cas il est `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key>  
    ref class set  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Touche  
 Le type du composant clé d’un élément dans la séquence contrôlée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[set::const_iterator (STL/CLR)](../dotnet/set-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[set::const_reference (STL/CLR)](../dotnet/set-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[set::const_reverse_iterator (STL/CLR)](../dotnet/set-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[set::difference_type (STL/CLR)](../dotnet/set-difference-type-stl-clr.md)|Le type d’une distance (éventuellement signée) entre deux éléments.|  
|[set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[set::generic_iterator (STL/CLR)](../dotnet/set-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[set::generic_reverse_iterator (STL/CLR)](../dotnet/set-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[set::generic_value (STL/CLR)](../dotnet/set-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)|Délégué de classement pour les deux clés.|  
|[set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)|Type d'une clé de tri.|  
|[set::reference (STL/CLR)](../dotnet/set-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[set::reverse_iterator (STL/CLR)](../dotnet/set-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[set::size_type (STL/CLR)](../dotnet/set-size-type-stl-clr.md)|Le type d’une distance (négatif) entre deux éléments.|  
|[set::value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)|Délégué de classement pour les deux valeurs d’éléments.|  
|[set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[set::begin (STL/CLR)](../dotnet/set-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[set::clear (STL/CLR)](../dotnet/set-clear-stl-clr.md)|Supprime tous les éléments.|  
|[set::count (STL/CLR)](../dotnet/set-count-stl-clr.md)|Compte des éléments qui correspondent à une clé spécifiée.|  
|[set::empty (STL/CLR)](../dotnet/set-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[set::equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)|Recherche une plage qui correspond à une clé spécifiée.|  
|[set::erase (STL/CLR)](../dotnet/set-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[set::find (STL/CLR)](../dotnet/set-find-stl-clr.md)|Recherche un élément qui correspond à une clé spécifiée.|  
|[set::insert (STL/CLR)](../dotnet/set-insert-stl-clr.md)|Ajoute des éléments.|  
|[set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)|Copie le délégué de classement pour les deux clés.|  
|[set::lower_bound (STL/CLR)](../dotnet/set-lower-bound-stl-clr.md)|Début de la recherche de plage qui correspond à une clé spécifiée.|  
|[set::make_value (STL/CLR)](../dotnet/set-make-value-stl-clr.md)|Construit un objet de valeur.|  
|[set::rbegin (STL/CLR)](../dotnet/set-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[set::rend (STL/CLR)](../dotnet/set-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[set::set (STL/CLR)](../dotnet/set-set-stl-clr.md)|Construit un objet conteneur.|  
|[set::size (STL/CLR)](../dotnet/set-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[set::swap (STL/CLR)](../dotnet/set-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[set::to_array (STL/CLR)](../dotnet/set-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)|Fin de la recherche de plage qui correspond à une clé spécifiée.|  
|[set::value_comp (STL/CLR)](../dotnet/set-value-comp-stl-clr.md)|Copie le délégué de classement pour les deux valeurs d’éléments.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator!= (set) (STL/CLR)](../dotnet/operator-inequality-set-stl-clr.md)|Détermine si un `set` objet n’est pas égal à un autre `set` objet.|  
|[operator< (set) (STL/CLR)](../dotnet/operator-less-than-set-stl-clr.md)|Détermine si un `set` objet est inférieur à un autre `set` objet.|  
|[operator<= (set) (STL/CLR)](../dotnet/operator-less-or-equal-set-stl-clr.md)|Détermine si un `set` objet est inférieur ou égal à un autre `set` objet.|  
|[operator== (set) (STL/CLR)](../dotnet/operator-equality-set-stl-clr.md)|Détermine si un `set` objet est égal à un autre `set` objet.|  
|[operator> (set) (STL/CLR)](../dotnet/operator-greater-than-set-stl-clr.md)|Détermine si un `set` objet est supérieur à un autre `set` objet.|  
|[operator>= (set) (STL/CLR)](../dotnet/operator-greater-or-equal-set-stl-clr.md)|Détermine si un `set` objet est supérieur ou égal à un autre `set` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|ITree\<de clé, la valeur >|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels. Il insère des éléments dans une arborescence à charge équilibrée (presque) il conserve ordonnée en modifiant les liens entre les nœuds, jamais par copie le contenu d’un nœud vers un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber éléments restants.  
  
 L’objet ordonne la séquence qu’il contrôle en appelant un objet délégué stocké de type [set::key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez le jeu ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(key_type, key_type)`. Pour accéder à cet objet stocké en appelant la fonction membre [set::key_comp (STL/CLR)](../dotnet/set-key-comp-stl-clr.md)`()`.  
  
 Cet objet de délégué doit imposer un classement faible strict sur les clés de type [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `key_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `key_comp()(X, Y)` est true, puis `key_comp()(Y, X)` doit avoir la valeur false.  
  
 Si `key_comp()(X, Y)` est true, puis `X` on dit d’être classé avant `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` est true, puis `X` et `Y` sont considérés comme ayant un classement équivalent.  
  
 Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés jamais diminuent dans valeur.) Contrairement à la classe de modèle [définir](../dotnet/set-stl-clr.md), un objet de classe de modèle `set` ne nécessite pas que les clés pour tous les éléments sont uniques. (Deux touches ou plus peuvent avoir un classement équivalent.)  
  
 Chaque élément sert à la fois une clé et une valeur. La séquence est représentée de façon à permettre la recherche, l’insertion et la suppression d’un élément arbitraire avec un nombre d’opérations proportionnels au logarithme du nombre d’éléments dans la séquence (temps logarithmique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
 Un ensemble prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents donnés d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [set::end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur ensemble afin d’atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément de jeu directement donné sa position numérique--nécessitant un itérateur à accès aléatoire.  
  
 Un itérateur ensemble stocke un handle vers son nœud de jeu associé, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Un itérateur ensemble reste valide tant que son nœud de jeu associé est associé à un ensemble. En outre, un itérateur valide est dereferencable : vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [set](../dotnet/set-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
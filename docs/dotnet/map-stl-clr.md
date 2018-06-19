---
title: carte (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cda679ed01e5266f0605639df45940d8f17e506d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137788"
---
# <a name="map-stlclr"></a>map (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès bidirectionnel. Vous utilisez le conteneur `map` pour gérer une séquence d’éléments sous forme d’arborescence triée à charge équilibrée (presque) des nœuds, chacun stocker un élément. Un élément est constitué d’une clé, pour le classement de la séquence et une valeur mappée, qui aborde le long de la conduite.  
  
 Dans la description ci-dessous, `GValue` est identique à :  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 où :  
  
 `GKey` est le même que `Key` , sauf si ce dernier est un type référence, auquel cas il est `Key^`  
  
 `GMapped` est le même que `Mapped` , sauf si ce dernier est un type référence, auquel cas il est `Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Touche  
 Le type du composant clé d’un élément dans la séquence contrôlée.  
  
 mappé  
 Le type du composant supplémentaire d’un élément dans la séquence contrôlée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[map::const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[map::const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[map::difference_type (STL/CLR)](../dotnet/map-difference-type-stl-clr.md)|Le type d’une distance (éventuellement signée) entre deux éléments.|  
|[map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[map::generic_iterator (STL/CLR)](../dotnet/map-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[map::generic_reverse_iterator (STL/CLR)](../dotnet/map-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[map::generic_value (STL/CLR)](../dotnet/map-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[map::iterator (STL/CLR)](../dotnet/map-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)|Délégué de classement pour les deux clés.|  
|[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)|Type d'une clé de tri.|  
|[map::mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)|Le type de la valeur mappée associée à chaque clé.|  
|[map::reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[map::size_type (STL/CLR)](../dotnet/map-size-type-stl-clr.md)|Le type d’une distance (négatif) entre deux éléments.|  
|[map::value_compare (STL/CLR)](../dotnet/map-value-compare-stl-clr.md)|Délégué de classement pour les deux valeurs d’éléments.|  
|[map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[map::clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)|Supprime tous les éléments.|  
|[map::count (STL/CLR)](../dotnet/map-count-stl-clr.md)|Compte des éléments qui correspondent à une clé spécifiée.|  
|[map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)|Recherche une plage qui correspond à une clé spécifiée.|  
|[map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[map::find (STL/CLR)](../dotnet/map-find-stl-clr.md)|Recherche un élément qui correspond à une clé spécifiée.|  
|[map::insert (STL/CLR)](../dotnet/map-insert-stl-clr.md)|Ajoute des éléments.|  
|[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)|Copie le délégué de classement pour les deux clés.|  
|[map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)|Début de la recherche de plage qui correspond à une clé spécifiée.|  
|[map::make_value (STL/CLR)](../dotnet/map-make-value-stl-clr.md)|Construit un objet de valeur.|  
|[map::map (STL/CLR)](../dotnet/map-map-stl-clr.md)|Construit un objet conteneur.|  
|[map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[map::swap (STL/CLR)](../dotnet/map-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[map::to_array (STL/CLR)](../dotnet/map-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)|Fin de la recherche de plage qui correspond à une clé spécifiée.|  
|[map::value_comp (STL/CLR)](../dotnet/map-value-comp-stl-clr.md)|Copie le délégué de classement pour les deux valeurs d’éléments.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[map::operator(STL/CLR)](../dotnet/map-operator-stl-clr.md)|Mappe une clé à sa valeur mappée associée.|  
|[operator!= (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)|Détermine si un `map` objet n’est pas égal à un autre `map` objet.|  
|[operator< (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)|Détermine si un `map` objet est inférieur à un autre `map` objet.|  
|[operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)|Détermine si un `map` objet est inférieur ou égal à un autre `map` objet.|  
|[operator== (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)|Détermine si un `map` objet est égal à un autre `map` objet.|  
|[operator> (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)|Détermine si un `map` objet est supérieur à un autre `map` objet.|  
|[operator>= (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|Détermine si un `map` objet est supérieur ou égal à un autre `map` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|<xref:System.Collections.Generic.IDictionary%602>|Mettre à jour le groupe de {clé, valeur} paires.|  
|ITree < clé, valeur >|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels. Il insère des éléments dans une arborescence à charge équilibrée (presque) il conserve ordonnée en modifiant les liens entre les nœuds, jamais par copie le contenu d’un nœud vers un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber éléments restants.  
  
 L’objet ordonne la séquence qu’il contrôle en appelant un objet délégué stocké de type [map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez l’objet map. Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(key_type, key_type)`. Pour accéder à cet objet stocké en appelant la fonction membre [map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`.  
  
 Cet objet de délégué doit imposer un classement faible strict sur les clés de type [map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `key_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `key_comp()(X, Y)` est true, puis `key_comp()(Y, X)` doit avoir la valeur false.  
  
 Si `key_comp()(X, Y)` est true, puis `X` on dit d’être classé avant `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` est true, puis `X` et `Y` sont considérés comme ayant un classement équivalent.  
  
 Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés jamais diminuent dans valeur.) Contrairement à la classe de modèle [carte](../dotnet/map-stl-clr.md), un objet de classe de modèle `map` ne nécessite pas que les clés pour tous les éléments sont uniques. (Deux touches ou plus peuvent avoir un classement équivalent.)  
  
 Chaque élément contient une clé séparée et une valeur mappée. La séquence est représentée de façon à permettre la recherche, l’insertion et la suppression d’un élément arbitraire avec un nombre d’opérations proportionnels au logarithme du nombre d’éléments dans la séquence (temps logarithmique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
 Une carte prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents donnés d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de la carte afin d’atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément cartographique directement donné sa position numérique--nécessitant un itérateur à accès aléatoire.  
  
 Un itérateur de la carte stocke un handle vers son nœud mappage associé, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Un itérateur de la carte est valide tant que son nœud mappage associé est associé à une classe map. En outre, un itérateur valide est dereferencable : vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [carte](../dotnet/map-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
---
title: multimap (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multimap
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 168c6afec0f8f195d1315a54eff2794f7e3fd07e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137915"
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès bidirectionnel. Vous utilisez le conteneur `multimap` pour gérer une séquence d’éléments sous forme d’arborescence triée à charge équilibrée (presque) des nœuds, chacun stocker un élément. Un élément est constitué d’une clé, pour le classement de la séquence et une valeur mappée, qui aborde le long de la conduite.  
  
 Dans la description ci-dessous, `GValue` est identique à :  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 où :  
  
 `GKey` est le même que `Key` , sauf si ce dernier est un type référence, auquel cas il est `Key^`  
  
 `GMapped` est le même que `Mapped` , sauf si ce dernier est un type référence, auquel cas il est `Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
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
  
 mappé  
 Le type du composant supplémentaire d’un élément dans la séquence contrôlée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[multimap::const_iterator (STL/CLR)](../dotnet/multimap-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[multimap::const_reverse_iterator (STL/CLR)](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[multimap::difference_type (STL/CLR)](../dotnet/multimap-difference-type-stl-clr.md)|Le type d’une distance (éventuellement signée) entre deux éléments.|  
|[multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[multimap::generic_iterator (STL/CLR)](../dotnet/multimap-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[multimap::generic_reverse_iterator (STL/CLR)](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[multimap::generic_value (STL/CLR)](../dotnet/multimap-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)|Délégué de classement pour les deux clés.|  
|[multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)|Type d'une clé de tri.|  
|[multimap::mapped_type (STL/CLR)](../dotnet/multimap-mapped-type-stl-clr.md)|Le type de la valeur mappée associée à chaque clé.|  
|[multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[multimap::reverse_iterator (STL/CLR)](../dotnet/multimap-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[multimap::size_type (STL/CLR)](../dotnet/multimap-size-type-stl-clr.md)|Le type d’une distance (négatif) entre deux éléments.|  
|[multimap::value_compare (STL/CLR)](../dotnet/multimap-value-compare-stl-clr.md)|Délégué de classement pour les deux valeurs d’éléments.|  
|[multimap::value_type (STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)|Supprime tous les éléments.|  
|[multimap::count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)|Compte des éléments qui correspondent à une clé spécifiée.|  
|[multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[multimap::equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)|Recherche une plage qui correspond à une clé spécifiée.|  
|[multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[multimap::find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)|Recherche un élément qui correspond à une clé spécifiée.|  
|[multimap::insert (STL/CLR)](../dotnet/multimap-insert-stl-clr.md)|Ajoute des éléments.|  
|[multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)|Copie le délégué de classement pour les deux clés.|  
|[multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)|Début de la recherche de plage qui correspond à une clé spécifiée.|  
|[multimap::make_value (STL/CLR)](../dotnet/multimap-make-value-stl-clr.md)|Construit un objet de valeur.|  
|[multimap::multimap (STL/CLR)](../dotnet/multimap-multimap-stl-clr.md)|Construit un objet conteneur.|  
|[multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[multimap::rend (STL/CLR)](../dotnet/multimap-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[multimap::swap (STL/CLR)](../dotnet/multimap-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[multimap::to_array (STL/CLR)](../dotnet/multimap-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)|Fin de la recherche de plage qui correspond à une clé spécifiée.|  
|[multimap::value_comp (STL/CLR)](../dotnet/multimap-value-comp-stl-clr.md)|Copie le délégué de classement pour les deux valeurs d’éléments.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator!= (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)|Détermine si un `multimap` objet n’est pas égal à un autre `multimap` objet.|  
|[operator< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)|Détermine si un `multimap` objet est inférieur à un autre `multimap` objet.|  
|[operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|Détermine si un `multimap` objet est inférieur ou égal à un autre `multimap` objet.|  
|[operator== (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)|Détermine si un `multimap` objet est égal à un autre `multimap` objet.|  
|[operator> (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)|Détermine si un `multimap` objet est supérieur à un autre `multimap` objet.|  
|[operator>= (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|Détermine si un `multimap` objet est supérieur ou égal à un autre `multimap` objet.|  
  
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
  
 L’objet ordonne la séquence qu’il contrôle en appelant un objet délégué stocké de type [multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lors de la construction du mappage multiple ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(key_type, key_type)`. Pour accéder à cet objet stocké en appelant la fonction membre [multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`.  
  
 Cet objet de délégué doit imposer un classement faible strict sur les clés de type [multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `key_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `key_comp()(X, Y)` est true, puis `key_comp()(Y, X)` doit avoir la valeur false.  
  
 Si `key_comp()(X, Y)` est true, puis `X` on dit d’être classé avant `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` est true, puis `X` et `Y` sont considérés comme ayant un classement équivalent.  
  
 Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés jamais diminuent dans valeur.) Contrairement à la classe de modèle [carte (STL/CLR)](../dotnet/map-stl-clr.md), un objet de classe de modèle `multimap` ne nécessite pas que les clés pour tous les éléments sont uniques. (Deux touches ou plus peuvent avoir un classement équivalent.)  
  
 Chaque élément contient une clé séparée et une valeur mappée. La séquence est représentée de façon à permettre la recherche, l’insertion et la suppression d’un élément arbitraire avec un nombre d’opérations proportionnels au logarithme du nombre d’éléments dans la séquence (temps logarithmique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
 Une classe multimap prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents donnés d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur multimap afin d’atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément multimap directement donné sa position numérique--nécessitant un itérateur à accès aléatoire.  
  
 Un itérateur multimap stocke un handle vers son nœud multimap associé, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Un itérateur multimap reste valide tant que son nœud multimap associé est associé à une classe multimap. En outre, un itérateur valide est dereferencable : vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
---
title: multiset (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e01ec2d9c426d6b95b12fe0db9e5a2e328ae1cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138481"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès bidirectionnel. Vous utilisez le conteneur `multiset` pour gérer une séquence d’éléments sous forme d’arborescence triée à charge équilibrée (presque) des nœuds, chacun stocker un élément.  
  
 Dans la description ci-dessous, `GValue` est identique à `GKey`, qui à son tour est le même que `Key` , sauf si ce dernier est un type référence, auquel cas il est `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key>  
    ref class multiset  
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
|[multiset::const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[multiset::const_reference (STL/CLR)](../dotnet/multiset-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[multiset::const_reverse_iterator (STL/CLR)](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[multiset::difference_type (STL/CLR)](../dotnet/multiset-difference-type-stl-clr.md)|Le type d’une distance (éventuellement signée) entre deux éléments.|  
|[multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[multiset::generic_iterator (STL/CLR)](../dotnet/multiset-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[multiset::generic_reverse_iterator (STL/CLR)](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[multiset::generic_value (STL/CLR)](../dotnet/multiset-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)|Délégué de classement pour les deux clés.|  
|[multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)|Type d'une clé de tri.|  
|[multiset::reference (STL/CLR)](../dotnet/multiset-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[multiset::reverse_iterator (STL/CLR)](../dotnet/multiset-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[multiset::size_type (STL/CLR)](../dotnet/multiset-size-type-stl-clr.md)|Le type d’une distance (négatif) entre deux éléments.|  
|[multiset::value_compare (STL/CLR)](../dotnet/multiset-value-compare-stl-clr.md)|Délégué de classement pour les deux valeurs d’éléments.|  
|[multiset::value_type (STL/CLR)](../dotnet/multiset-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)|Supprime tous les éléments.|  
|[multiset::count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)|Compte des éléments qui correspondent à une clé spécifiée.|  
|[multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[multiset::equal_range (STL/CLR)](../dotnet/multiset-equal-range-stl-clr.md)|Recherche une plage qui correspond à une clé spécifiée.|  
|[multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[multiset::find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)|Recherche un élément qui correspond à une clé spécifiée.|  
|[multiset::insert (STL/CLR)](../dotnet/multiset-insert-stl-clr.md)|Ajoute des éléments.|  
|[multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)|Copie le délégué de classement pour les deux clés.|  
|[multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)|Début de la recherche de plage qui correspond à une clé spécifiée.|  
|[multiset::make_value (STL/CLR)](../dotnet/multiset-make-value-stl-clr.md)|Construit un objet de valeur.|  
|[multiset::multiset (STL/CLR)](../dotnet/multiset-multiset-stl-clr.md)|Construit un objet conteneur.|  
|[multiset::rbegin (STL/CLR)](../dotnet/multiset-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[multiset::rend (STL/CLR)](../dotnet/multiset-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[multiset::swap (STL/CLR)](../dotnet/multiset-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[multiset::to_array (STL/CLR)](../dotnet/multiset-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)|Fin de la recherche de plage qui correspond à une clé spécifiée.|  
|[multiset::value_comp (STL/CLR)](../dotnet/multiset-value-comp-stl-clr.md)|Copie le délégué de classement pour les deux valeurs d’éléments.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator!= (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)|Détermine si un `multiset` objet n’est pas égal à un autre `multiset` objet.|  
|[operator< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)|Détermine si un `multiset` objet est inférieur à un autre `multiset` objet.|  
|[operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|Détermine si un `multiset` objet est inférieur ou égal à un autre `multiset` objet.|  
|[operator== (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)|Détermine si un `multiset` objet est égal à un autre `multiset` objet.|  
|[operator> (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)|Détermine si un `multiset` objet est supérieur à un autre `multiset` objet.|  
|[operator>= (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|Détermine si un `multiset` objet est supérieur ou égal à un autre `multiset` objet.|  
  
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
  
 L’objet ordonne la séquence qu’il contrôle en appelant un objet délégué stocké de type [multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lors de la construction de la classe multiset ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(key_type, key_type)`. Pour accéder à cet objet stocké en appelant la fonction membre [multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`.  
  
 Cet objet de délégué doit imposer un classement faible strict sur les clés de type [multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `key_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `key_comp()(X, Y)` est true, puis `key_comp()(Y, X)` doit avoir la valeur false.  
  
 Si `key_comp()(X, Y)` est true, puis `X` on dit d’être classé avant `Y`.  
  
 Si `!key_comp()(X, Y) && !key_comp()(Y, X)` est true, puis `X` et `Y` sont considérés comme ayant un classement équivalent.  
  
 Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés jamais diminuent dans valeur.) Contrairement à la classe de modèle [(STL/CLR) de définir](../dotnet/set-stl-clr.md), un objet de classe de modèle `multiset` ne nécessite pas que les clés pour tous les éléments sont uniques. (Deux touches ou plus peuvent avoir un classement équivalent.)  
  
 Chaque élément sert à la fois une clé et une valeur. La séquence est représentée de façon à permettre la recherche, l’insertion et la suppression d’un élément arbitraire avec un nombre d’opérations proportionnels au logarithme du nombre d’éléments dans la séquence (temps logarithmique). De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
 Un multiensemble prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents donnés d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de type multiset afin d’atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément de multiensemble directement donné sa position numérique--nécessitant un itérateur à accès aléatoire.  
  
 Un itérateur de type multiset stocke un handle vers son nœud multiset associé, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Un itérateur de type multiset reste valide tant que son nœud multiset associé est associé à une classe multiset. En outre, un itérateur valide est dereferencable : vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/set >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
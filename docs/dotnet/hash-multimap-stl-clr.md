---
title: hash_multimap (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multimap
dev_langs:
- C++
helpviewer_keywords:
- hash_multimap class [STL/CLR]
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
ms.assetid: cd78687b-8a05-48e0-9d22-8b8194ae3b0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 027ed43936e4335819f95d10050de37570e6a679
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137991"
---
# <a name="hashmultimap-stlclr"></a>hash_multimap (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès bidirectionnel. Vous utilisez le conteneur `hash_multimap` pour gérer une séquence d’éléments comme une table de hachage, chaque entrée de table stockant un bidirectionnel lié à la liste des nœuds et chaque nœud de stocker un élément. Un élément est constitué d’une clé, pour le classement de la séquence et une valeur mappée, qui aborde le long de la conduite.  
  
 Dans la description ci-dessous, `GValue` est identique à :  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 où :  
  
 `GKey` est le même que `Key` , sauf si ce dernier est un type référence, auquel cas il est `Key^`  
  
 `GMapped` est le même que `Mapped` , sauf si ce dernier est un type référence, auquel cas il est `Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_multimap  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
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
|[hash_multimap::const_iterator (STL/CLR)](../dotnet/hash-multimap-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[hash_multimap::const_reference (STL/CLR)](../dotnet/hash-multimap-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[hash_multimap::const_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[hash_multimap::difference_type (STL/CLR)](../dotnet/hash-multimap-difference-type-stl-clr.md)|Le type d’une distance (éventuellement signée) entre deux éléments.|  
|[hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[hash_multimap::generic_iterator (STL/CLR)](../dotnet/hash-multimap-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[hash_multimap::generic_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[hash_multimap::generic_value (STL/CLR)](../dotnet/hash-multimap-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[hash_multimap::hasher (STL/CLR)](../dotnet/hash-multimap-hasher-stl-clr.md)|Délégué d’une clé de hachage.|  
|[hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[hash_multimap::key_compare (STL/CLR)](../dotnet/hash-multimap-key-compare-stl-clr.md)|Délégué de classement pour les deux clés.|  
|[hash_multimap::key_type (STL/CLR)](../dotnet/hash-multimap-key-type-stl-clr.md)|Type d'une clé de tri.|  
|[hash_multimap::mapped_type (STL/CLR)](../dotnet/hash-multimap-mapped-type-stl-clr.md)|Le type de la valeur mappée associée à chaque clé.|  
|[hash_multimap::reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[hash_multimap::reverse_iterator (STL/CLR)](../dotnet/hash-multimap-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[hash_multimap::size_type (STL/CLR)](../dotnet/hash-multimap-size-type-stl-clr.md)|Le type d’une distance (négatif) entre deux éléments.|  
|[hash_multimap::value_compare (STL/CLR)](../dotnet/hash-multimap-value-compare-stl-clr.md)|Délégué de classement pour les deux valeurs d’éléments.|  
|[hash_multimap::value_type (STL/CLR)](../dotnet/hash-multimap-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[hash_multimap::begin (STL/CLR)](../dotnet/hash-multimap-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[hash_multimap::bucket_count (STL/CLR)](../dotnet/hash-multimap-bucket-count-stl-clr.md)|Compte le nombre de compartiments.|  
|[hash_multimap::clear (STL/CLR)](../dotnet/hash-multimap-clear-stl-clr.md)|Supprime tous les éléments.|  
|[hash_multimap::count (STL/CLR)](../dotnet/hash-multimap-count-stl-clr.md)|Compte des éléments qui correspondent à une clé spécifiée.|  
|[hash_multimap::empty (STL/CLR)](../dotnet/hash-multimap-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[hash_multimap::equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)|Recherche une plage qui correspond à une clé spécifiée.|  
|[hash_multimap::erase (STL/CLR)](../dotnet/hash-multimap-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[hash_multimap::find (STL/CLR)](../dotnet/hash-multimap-find-stl-clr.md)|Recherche un élément qui correspond à une clé spécifiée.|  
|[hash_multimap::hash_delegate (STL/CLR)](../dotnet/hash-multimap-hash-delegate-stl-clr.md)|Copie le délégué de hachage pour une clé.|  
|[hash_multimap::hash_multimap (STL/CLR)](../dotnet/hash-multimap-hash-multimap-stl-clr.md)|Construit un objet conteneur.|  
|[hash_multimap::insert (STL/CLR)](../dotnet/hash-multimap-insert-stl-clr.md)|Ajoute des éléments.|  
|[hash_multimap::key_comp (STL/CLR)](../dotnet/hash-multimap-key-comp-stl-clr.md)|Copie le délégué de classement pour les deux clés.|  
|[hash_multimap::load_factor (STL/CLR)](../dotnet/hash-multimap-load-factor-stl-clr.md)|Compte le nombre moyen d'éléments par compartiment.|  
|[hash_multimap::lower_bound (STL/CLR)](../dotnet/hash-multimap-lower-bound-stl-clr.md)|Début de la recherche de plage qui correspond à une clé spécifiée.|  
|[hash_multimap::make_value (STL/CLR)](../dotnet/hash-multimap-make-value-stl-clr.md)|Construit un objet de valeur.|  
|[hash_multimap::max_load_factor (STL/CLR)](../dotnet/hash-multimap-max-load-factor-stl-clr.md)|Obtient ou définit le nombre maximal d’éléments par compartiment.|  
|[hash_multimap::rbegin (STL/CLR)](../dotnet/hash-multimap-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[hash_multimap::rehash (STL/CLR)](../dotnet/hash-multimap-rehash-stl-clr.md)|Régénère la table de hachage.|  
|[hash_multimap::rend (STL/CLR)](../dotnet/hash-multimap-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[hash_multimap::size (STL/CLR)](../dotnet/hash-multimap-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[hash_multimap::swap (STL/CLR)](../dotnet/hash-multimap-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[hash_multimap::to_array (STL/CLR)](../dotnet/hash-multimap-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[hash_multimap::upper_bound (STL/CLR)](../dotnet/hash-multimap-upper-bound-stl-clr.md)|Fin de la recherche de plage qui correspond à une clé spécifiée.|  
|[hash_multimap::value_comp (STL/CLR)](../dotnet/hash-multimap-value-comp-stl-clr.md)|Copie le délégué de classement pour les deux valeurs d’éléments.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[hash_multimap::operator= (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|IHash\<de clé, la valeur >|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels dans une liste liée bidirectionnelle. Pour accélérer l’accès, l’objet conserve un tableau de longueur variable de pointeurs dans la liste (la table de hachage), gestion efficace de l’intégralité de la liste comme une séquence de sous-listes, ou compartiments. Elle insère des éléments dans un compartiment il conserve ordonnée en modifiant les liens entre les nœuds, jamais par copie le contenu d’un nœud vers un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber éléments restants.  
  
 Chaque compartiment qu’il contrôle en appelant un objet délégué stocké de type des commandes de l’objet [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez l’objet hash_set ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<=(key_type, key_type)`.  
  
 Pour accéder à l’objet délégué stockée en appelant la fonction membre [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Cet objet de délégué doit définir un classement équivalent entre les clés de type [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `key_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `key_comp()(X, Y) && key_comp()(Y, X)` est true, puis `X` et `Y` sont considérés comme ayant un classement équivalent.  
  
 Une règle de tri qui se comporte comme `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` ou `operator==(key_type, key_type)` définit l’ordre d’eqivalent.  
  
 Notez que le conteneur garantit uniquement qu’éléments dont les clés ont un classement équivalent (et le hachage à la même valeur d’entier) sont adjacents dans un compartiment. Contrairement à la classe de modèle [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md), un objet de classe de modèle `hash_multimap` ne nécessite pas que les clés pour tous les éléments sont uniques. (Deux touches ou plus peuvent avoir un classement équivalent.)  
  
 L’objet détermine quel compartiment doit contenir une clé de tri spécifique en appelant un objet délégué stocké de type [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Pour accéder à cet objet stocké en appelant la fonction membre [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` pour obtenir une valeur entière qui dépend de la valeur de clé. Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez l’objet hash_set ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la fonction `System::Object::hash_value(key_type)`. Cela signifie que, pour toutes les clés `X` et `Y`:  
  
 `hash_delegate()(X)` Retourne le même résultat entier sur chaque appel.  
  
 Si `X` et `Y` ont un classement équivalent, puis `hash_delegate()(X)` doit retourner le même résultat entier en tant que `hash_delegate()(Y)`.  
  
 Chaque élément contient une clé séparée et une valeur mappée. La séquence est représentée d’une façon qui permet la recherche, l’insertion et la suppression d’un élément arbitraire avec un nombre d’opérations qui est indépendant du nombre d’éléments dans la séquence (temps constant)--au moins dans le meilleur des cas. De plus, l'insertion d'un élément n'entraîne pas la non validité des itérateurs, et la suppression d'un élément ne rend non valides que les itérateurs qui pointent vers l'élément supprimé.  
  
 Toutefois, si les valeurs de hachage ne sont pas distribuées uniformément, une table de hachage peut dégénérées. À l’extrême--pour une fonction de hachage qui retourne toujours la même valeur--recherche, d’insertion et de suppression sont proportionnelles au nombre d’éléments dans la séquence (délai linéaire). Le conteneur s’efforce de choisir une fonction de hachage raisonnable, la taille du compartiment moyenne et taille de la table de hachage (nombre total de compartiments), mais vous pouvez remplacer tout ou partie de ces choix. Voir, par exemple, les fonctions [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) et [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Un objet hash_multimap prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents donnés d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur hash_multimap afin d’atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément de hash_multimap directement donné sa position numérique--nécessitant un itérateur à accès aléatoire.  
  
 Un itérateur hash_multimap stocke un handle vers son nœud hash_multimap associé, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Un itérateur hash_multimap reste valide tant que son nœud associé hash_multimap est associé à certaines hash_multimap. En outre, un itérateur valide est dereferencable : vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/hash_map >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [carte (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
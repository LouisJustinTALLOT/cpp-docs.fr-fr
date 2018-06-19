---
title: liste (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4ff009da3ca29697e9b3affceb424bcd84b9b896
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33141748"
---
# <a name="list-stlclr"></a>list (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence de longueur variable d’éléments ayant un accès bidirectionnel. Vous utilisez le conteneur `list` pour gérer une séquence d’éléments comme une liste liée bidirectionnelle de nœuds, chacun stocker un élément.  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Value  
 Type d'un élément dans la séquence contrôlée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](../dotnet/list-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[list::const_reference (STL/CLR)](../dotnet/list-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[list::const_reverse_iterator (STL/CLR)](../dotnet/list-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[list::difference_type (STL/CLR)](../dotnet/list-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[list::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[list::generic_iterator (STL/CLR)](../dotnet/list-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[list::generic_reverse_iterator (STL/CLR)](../dotnet/list-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[list::generic_value (STL/CLR)](../dotnet/list-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[list::iterator (STL/CLR)](../dotnet/list-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[list::reference (STL/CLR)](../dotnet/list-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[list::reverse_iterator (STL/CLR)](../dotnet/list-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[list::size_type (STL/CLR)](../dotnet/list-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[list::value_type (STL/CLR)](../dotnet/list-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)|Remplace tous les éléments.|  
|[list::back (STL/CLR)](../dotnet/list-back-stl-clr.md)|Accède au dernier élément.|  
|[list::begin (STL/CLR)](../dotnet/list-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)|Supprime tous les éléments.|  
|[list::empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[list::erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[list::front (STL/CLR)](../dotnet/list-front-stl-clr.md)|Accède au premier élément.|  
|[list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)|Ajoute des éléments à la position spécifiée.|  
|[list::list (STL/CLR)](../dotnet/list-list-stl-clr.md)|Construit un objet conteneur.|  
|[list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)|Fusionne deux séquences contrôlées ordonnées.|  
|[list::pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)|Supprime le dernier élément.|  
|[list::pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)|Supprime le premier élément.|  
|[list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)|Ajoute un nouvel élément en dernier.|  
|[list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)|Ajoute un nouvel élément en premier.|  
|[list::rbegin (STL/CLR)](../dotnet/list-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[list::remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)|Supprime un élément avec une valeur spécifiée.|  
|[list::remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)|Supprime les éléments qui réussissent un test spécifié.|  
|[list::rend (STL/CLR)](../dotnet/list-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[list::resize (STL/CLR)](../dotnet/list-resize-stl-clr.md)|Modifie le nombre d’éléments.|  
|[list::reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)|Inverse la séquence contrôlée.|  
|[list::size (STL/CLR)](../dotnet/list-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)|Ordonne la séquence contrôlée.|  
|[list::splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)|Réassocie les liens entre les nœuds.|  
|[list::swap (STL/CLR)](../dotnet/list-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[list::to_array (STL/CLR)](../dotnet/list-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)|Supprime des éléments adjacents qui réussissent un test spécifié.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](../dotnet/list-back-item-stl-clr.md)|Accède au dernier élément.|  
|[list::front_item (STL/CLR)](../dotnet/list-front-item-stl-clr.md)|Accède au premier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator!= (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)|Détermine si un `list` objet n’est pas égal à un autre `list` objet.|  
|[operator< (list) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)|Détermine si un `list` objet est inférieur à un autre `list` objet.|  
|[operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)|Détermine si un `list` objet est inférieur ou égal à un autre `list` objet.|  
|[operator== (list) (STL/CLR)](../dotnet/operator-equality-list-stl-clr.md)|Détermine si un `list` objet est égal à un autre `list` objet.|  
|[operator> (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)|Détermine si un `list` objet est supérieur à un autre `list` objet.|  
|[operator>= (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)|Détermine si un `list` objet est supérieur ou égal à un autre `list` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|IList\<valeur >|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle en tant que nœuds individuels dans une liste de liens bidirectionnel. Il réorganise les éléments en modifiant les liens entre les nœuds, jamais par copie le contenu d’un nœud vers un autre. Cela signifie que vous pouvez insérer et supprimer des éléments librement sans perturber éléments restants. Par conséquent, une liste est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [la file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md) ou classe de modèle [pile (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `list` objet prend en charge les itérateurs bidirectionnels, ce qui signifie que vous pouvez exécuter pour les éléments adjacents donnés d’un itérateur qui désigne un élément dans la séquence contrôlée. Un nœud principal spécial correspond à l’itérateur retourné par [list::end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`. Vous pouvez décrémenter cet itérateur afin d’atteindre le dernier élément dans la séquence contrôlée, le cas échéant. Vous pouvez incrémenter un itérateur de la liste afin d’atteindre le nœud principal, et il compare ensuite égal à `end()`. Mais vous ne pouvez pas déréférencer l’itérateur retourné par `end()`.  
  
 Notez que vous ne pouvez pas faire référence à un élément de liste directement donné sa position numérique--nécessitant un itérateur à accès aléatoire. Par conséquent, une liste est `not` utilisable en tant que conteneur pour la classe de modèle sous-jacent [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un itérateur de liste stocke un handle vers son nœud liste associée, qui à son tour stocke un handle à son conteneur associé. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Un itérateur de liste reste valide tant que son nœud liste associée est associé à une liste. En outre, un itérateur valide est dereferencable : vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant qu’il n’est pas égal à `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/liste >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pile (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
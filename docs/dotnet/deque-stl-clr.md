---
title: deque (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque
dev_langs:
- C++
helpviewer_keywords:
- deque class [STL/CLR]
- <deque> header [STL/CLR]
- <cliext/deque> header [STL/CLR]
ms.assetid: dd669da3-3c0e-45e9-8596-f6b483720941
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 11436466dadf4b06e604af6e2b5150a22c4ed241
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111144"
---
# <a name="deque-stlclr"></a>deque (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence à longueur variable d’éléments ayant un accès aléatoire. Vous utilisez le conteneur `deque` pour gérer une séquence d’éléments qui ressemble à un bloc contigu de stockage, mais qui peuvent augmenter ou réduire à chaque extrémité sans avoir besoin de copier les éléments restants. Par conséquent, elle peut implémenter efficacement un `double-ended queue`. (Par conséquent, le nom.)  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class deque  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IDeque<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 GValue  
 Le type générique d’un élément dans la séquence contrôlée.  
  
 Value  
 Type d'un élément dans la séquence contrôlée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[deque::const_iterator (STL/CLR)](../dotnet/deque-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[deque::const_reference (STL/CLR)](../dotnet/deque-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[deque::const_reverse_iterator (STL/CLR)](../dotnet/deque-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[deque::difference_type (STL/CLR)](../dotnet/deque-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[deque::generic_iterator (STL/CLR)](../dotnet/deque-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[deque::generic_reverse_iterator (STL/CLR)](../dotnet/deque-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[deque::generic_value (STL/CLR)](../dotnet/deque-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[deque::iterator (STL/CLR)](../dotnet/deque-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[deque::reference (STL/CLR)](../dotnet/deque-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[deque::reverse_iterator (STL/CLR)](../dotnet/deque-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[deque::size_type (STL/CLR)](../dotnet/deque-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[deque::value_type (STL/CLR)](../dotnet/deque-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[deque::assign (STL/CLR)](../dotnet/deque-assign-stl-clr.md)|Remplace tous les éléments.|  
|[deque::at (STL/CLR)](../dotnet/deque-at-stl-clr.md)|Accède à un élément à une position spécifiée.|  
|[deque::back (STL/CLR)](../dotnet/deque-back-stl-clr.md)|Accède au dernier élément.|  
|[deque::begin (STL/CLR)](../dotnet/deque-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[deque::clear (STL/CLR)](../dotnet/deque-clear-stl-clr.md)|Supprime tous les éléments.|  
|[deque::deque (STL/CLR)](../dotnet/deque-deque-stl-clr.md)|Construit un objet conteneur.|  
|[deque::empty (STL/CLR)](../dotnet/deque-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[deque::end (STL/CLR)](../dotnet/deque-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[deque::erase (STL/CLR)](../dotnet/deque-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[deque::front (STL/CLR)](../dotnet/deque-front-stl-clr.md)|Accède au premier élément.|  
|[deque::insert (STL/CLR)](../dotnet/deque-insert-stl-clr.md)|Ajoute des éléments à la position spécifiée.|  
|[deque::pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)|Supprime le dernier élément.|  
|[deque::pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)|Supprime le premier élément.|  
|[deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)|Ajoute un nouvel élément en dernier.|  
|[deque::push_front (STL/CLR)](../dotnet/deque-push-front-stl-clr.md)|Ajoute un nouvel élément en premier.|  
|[deque::rbegin (STL/CLR)](../dotnet/deque-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[deque::rend (STL/CLR)](../dotnet/deque-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[deque::resize (STL/CLR)](../dotnet/deque-resize-stl-clr.md)|Modifie le nombre d’éléments.|  
|[deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[deque::swap (STL/CLR)](../dotnet/deque-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[deque::to_array (STL/CLR)](../dotnet/deque-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[deque::back_item (STL/CLR)](../dotnet/deque-back-item-stl-clr.md)|Accède au dernier élément.|  
|[deque::front_item (STL/CLR)](../dotnet/deque-front-item-stl-clr.md)|Accède au premier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[deque::operator!= (STL/CLR)](../dotnet/deque-operator-inequality-stl-clr.md)|Détermine si deux `deque` objets ne sont pas égaux.|  
|[deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)|Accède à un élément à une position spécifiée.|  
|[operator< (deque) (STL/CLR)](../dotnet/operator-less-than-deque-stl-clr.md)|Détermine si un `deque` objet est inférieur à un autre `deque` objet.|  
|[operator<= (deque) (STL/CLR)](../dotnet/operator-less-or-equal-deque-stl-clr.md)|Détermine si un `deque` objet est inférieur ou égal à un autre `deque` objet.|  
|[operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator== (deque) (STL/CLR)](../dotnet/operator-equality-deque-stl-clr.md)|Détermine si un `deque` objet est égal à un autre `deque` objet.|  
|[operator> (deque) (STL/CLR)](../dotnet/operator-greater-than-deque-stl-clr.md)|Détermine si un `deque` objet est supérieur à un autre `deque` objet.|  
|[operator>= (deque) (STL/CLR)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)|Détermine si un `deque` objet est supérieur ou égal à un autre `deque` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|<xref:System.Collections.Generic.IList%601>|Mettre à jour un groupe ordonné d’éléments typés.|  
|IDeque < valeur\>|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un tableau stocké de handles qui désigne des blocs de `Value` éléments. Le module s’étend à la demande. Croissance se produit de manière à ce que le coût de l’ajoutant au début ou de l’ajout d’un nouvel élément est le temps constant, et aucuns autres éléments ne sont perturbés. Vous pouvez également supprimer un élément à des extrémités dans le temps et sans perturber éléments restants. Par conséquent, un deque est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [la file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md) ou classe de modèle [pile (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `deque` objet prend en charge les itérateurs à accès aléatoire, ce qui signifie que vous pouvez faire référence à un élément donné directement de sa position numérique, en partant de zéro pour le premier élément (avant), à [deque::size (STL/CLR)](../dotnet/deque-size-stl-clr.md) `() - 1` pour le dernier élément (précédent). Cela signifie également qu’un deque est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un itérateur deque stocke un handle vers son objet deque associés, ainsi que le décalage de l’élément qu’il désigne. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Le décalage d’un élément deque est `not` nécessairement identique à sa position. Le premier élément inséré a le décalage de zéro, l’élément ajouté suivant a POLARISATION 1, mais l’élément ajoutant au début suivant a écart -1.  
  
 Insertion ou la suppression d’éléments aux extrémités est `not` modifier la valeur d’un élément stocké sur n’importe quel décalage valide. Insertion ou suppression d’un élément intérieur, toutefois, `can` modifier la valeur d’élément stockée à un décalage donné, donc la valeur désignée par un itérateur peut également changer. (Le conteneur peut avoir à copier des éléments ou vers le bas pour créer une faille d’avant une opération d’insertion ou de remplissage d’un trou après un effacement.) Toutefois, un itérateur deque reste valide tant que son décalage désigne un élément valide. En outre, un itérateur valide reste dereferencable--vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant que son décalage n’est pas égal à l’écart de l’itérateur retourné par `end()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Toutefois, notez qu’un conteneur de handles ne `not` détruire ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/deque >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pile (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
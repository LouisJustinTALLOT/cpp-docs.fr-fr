---
title: vecteur (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de5d09d569933dc06666ed2008081703d59c1564
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172636"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence à longueur variable d’éléments ayant un accès aléatoire. Vous utilisez le conteneur `vector` pour gérer une séquence d’éléments comme un bloc contigu de stockage. Le bloc est implémenté comme un tableau dont la taille augmente à la demande.  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Value  
 Type d'un élément dans la séquence contrôlée.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)|Type d'un itérateur constant pour la séquence contrôlée.|  
|[vector::const_reference (STL/CLR)](../dotnet/vector-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[vector::const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)|Type d'un itérateur inserve constant pour la séquence contrôlée.|  
|[vector::difference_type (STL/CLR)](../dotnet/vector-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)|Le type de l’interface générique pour le conteneur.|  
|[vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)|Le type d’un itérateur pour l’interface générique pour le conteneur.|  
|[vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)|Le type d’un itérateur inverse pour l’interface générique pour le conteneur.|  
|[vector::generic_value (STL/CLR)](../dotnet/vector-generic-value-stl-clr.md)|Le type d’un élément pour l’interface générique pour le conteneur.|  
|[vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)|Type d'un itérateur pour la séquence contrôlée.|  
|[vector::reference (STL/CLR)](../dotnet/vector-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[vector::reverse_iterator (STL/CLR)](../dotnet/vector-reverse-iterator-stl-clr.md)|Type d'un itérateur inverse pour la séquence contrôlée.|  
|[vector::size_type (STL/CLR)](../dotnet/vector-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[vector::value_type (STL/CLR)](../dotnet/vector-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)|Remplace tous les éléments.|  
|[vector::at (STL/CLR)](../dotnet/vector-at-stl-clr.md)|Accède à un élément à une position spécifiée.|  
|[vector::back (STL/CLR)](../dotnet/vector-back-stl-clr.md)|Accède au dernier élément.|  
|[vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md)|Désigne le début de la séquence contrôlée.|  
|[vector::capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)|Indique la taille de stockage alloué pour le conteneur.|  
|[vector::clear (STL/CLR)](../dotnet/vector-clear-stl-clr.md)|Supprime tous les éléments.|  
|[vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md)|Désigne la fin de la séquence contrôlée.|  
|[vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)|Supprime les éléments placés aux positions spécifiées.|  
|[vector::front (STL/CLR)](../dotnet/vector-front-stl-clr.md)|Accède au premier élément.|  
|[vector::insert (STL/CLR)](../dotnet/vector-insert-stl-clr.md)|Ajoute des éléments à la position spécifiée.|  
|[vector::pop_back (STL/CLR)](../dotnet/vector-pop-back-stl-clr.md)|Supprime le dernier élément.|  
|[vector::push_back (STL/CLR)](../dotnet/vector-push-back-stl-clr.md)|Ajoute un nouvel élément en dernier.|  
|[vector::rbegin (STL/CLR)](../dotnet/vector-rbegin-stl-clr.md)|Désigne le début de la séquence contrôlée inverse.|  
|[vector::rend (STL/CLR)](../dotnet/vector-rend-stl-clr.md)|Désigne la fin de la séquence contrôlée inverse.|  
|[vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)|Garantit une capacité minimale de croissance pour le conteneur.|  
|[vector::resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)|Modifie le nombre d’éléments.|  
|[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[vector::swap (STL/CLR)](../dotnet/vector-swap-stl-clr.md)|Échange le contenu de deux conteneurs.|  
|[vector::to_array (STL/CLR)](../dotnet/vector-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[vector::vector (STL/CLR)](../dotnet/vector-vector-stl-clr.md)|Construit un objet conteneur.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](../dotnet/vector-back-item-stl-clr.md)|Accède au dernier élément.|  
|[vector::front_item (STL/CLR)](../dotnet/vector-front-item-stl-clr.md)|Accède au premier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[vector::operator(STL/CLR)](../dotnet/vector-operator-stl-clr.md)|Accède à un élément à une position spécifiée.|  
|[operator!= (vector) (STL/CLR)](../dotnet/operator-inequality-vector-stl-clr.md)|Détermine si un `vector` objet n’est pas égal à un autre `vector` objet.|  
|[operator< (vector) (STL/CLR)](../dotnet/operator-less-than-vector-stl-clr.md)|Détermine si un `vector` objet est inférieur à un autre `vector` objet.|  
|[operator<= (vector) (STL/CLR)](../dotnet/operator-less-or-equal-vector-stl-clr.md)|Détermine si un `vector` objet est inférieur ou égal à un autre `vector` objet.|  
|[operator== (vector) (STL/CLR)](../dotnet/operator-equality-vector-stl-clr.md)|Détermine si un `vector` objet est égal à un autre `vector` objet.|  
|[operator> (vector) (STL/CLR)](../dotnet/operator-greater-than-vector-stl-clr.md)|Détermine si un `vector` objet est supérieur à un autre `vector` objet.|  
|[operator>= (vector) (STL/CLR)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)|Détermine si un `vector` objet est supérieur ou égal à un autre `vector` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|<xref:System.Collections.IEnumerable>|Dans les éléments de séquence.|  
|<xref:System.Collections.ICollection>|Conserver le groupe d’éléments.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Séquence via les éléments typés.|  
|<xref:System.Collections.Generic.ICollection%601>|Conserver le groupe d’éléments typés.|  
|<xref:System.Collections.Generic.IList%601>|Mettre à jour un groupe ordonné d’éléments typés.|  
|IVector < valeur\>|Mettre à jour de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un tableau stocké de `Value` éléments, ce qui se développe sur la demande. Croissance se produit de manière à ce que le coût de l’ajout d’un nouvel élément est le temps fixe amorti. En d’autres termes, le coût de l’ajout d’éléments à la fin n’augmente pas, en moyenne, en tant que la longueur des séquence contrôlée est élevé. Par conséquent, un vecteur est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [pile (STL/CLR)](../dotnet/stack-stl-clr.md).  
  
 A `vector` itérateurs prend en charge l’accès aléatoire, ce qui signifie que vous pouvez faire référence à un élément donné directement de sa position numérique, en partant de zéro pour le premier élément (avant), à `size() - 1` pour le dernier élément (arrière). Cela signifie également qu’un vecteur est un bon candidat pour le conteneur sous-jacent pour la classe de modèle [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md).  
  
 Un itérateur de vecteur stocke un handle vers son objet de vecteur associés, ainsi que le décalage de l’élément qu’il désigne. Vous pouvez utiliser des itérateurs uniquement avec les objets du conteneur associé. Le décalage d’un élément de vecteur est identique à sa position.  
  
 Insertion ou la suppression d’éléments pouvez modifier la valeur d’élément stockée à une position donnée, de sorte que la valeur désignée par un itérateur peut également changer. (Le conteneur peut avoir à copier des éléments ou vers le bas pour créer une faille d’avant une opération d’insertion ou de remplissage d’un trou après un effacement.) Toutefois, un itérateur de vecteur reste valide tant que son décalage est dans la plage `[0, size()]`. En outre, un itérateur valide reste dereferencable--vous pouvez l’utiliser pour accéder ou modifier la valeur d’élément qu’il désigne--tant que son décalage n’est pas égal à `size()`.  
  
 Effacement ou suppression d’un élément appelle le destructeur de sa valeur stockée. Destruction du conteneur efface tous les éléments. Par conséquent, un conteneur dont le type d’élément est une classe ref garantit qu’aucun élément ne survivent le conteneur. Notez, toutefois, qu’un conteneur de handles ne détruit pas ses éléments.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/vector >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pile (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)  
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
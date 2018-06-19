---
title: file d’attente (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue
dev_langs:
- C++
helpviewer_keywords:
- <queue> header [STL/CLR]
- queue class [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 9ea7dec3-ea98-48ff-87d0-a5afc924aaf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e65d5a364f5886df2bad976e3c34dc57266b70f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172742"
---
# <a name="queue-stlclr"></a>queue (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence à longueur variable d’éléments qui dispose d’un accès premier sorti. Utilisation de l’adaptateur de conteneur `queue` pour gérer un conteneur sous-jacent comme une file d’attente.  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`. De même, `GContainer` est identique à `Container` , sauf si ce dernier est un type référence, auquel cas il est `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    ref class queue  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IQueue<GValue, GContainer>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Paramètres  
 Value  
 Type d'un élément dans la séquence contrôlée.  
  
 Conteneur  
 Type du conteneur sous-jacent.  
  
## <a name="members"></a>Membres  
  
|Définition de types|Description|  
|---------------------|-----------------|  
|[queue::const_reference (STL/CLR)](../dotnet/queue-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)|Type du conteneur sous-jacent.|  
|[queue::difference_type (STL/CLR)](../dotnet/queue-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)|Le type de l’interface générique pour l’adaptateur de conteneur.|  
|[queue::generic_value (STL/CLR)](../dotnet/queue-generic-value-stl-clr.md)|Le type d’un élément de l’interface générique de l’adaptateur de conteneur.|  
|[queue::reference (STL/CLR)](../dotnet/queue-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[queue::size_type (STL/CLR)](../dotnet/queue-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)|Remplace tous les éléments.|  
|[queue::back (STL/CLR)](../dotnet/queue-back-stl-clr.md)|Accède au dernier élément.|  
|[queue::empty (STL/CLR)](../dotnet/queue-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[queue::front (STL/CLR)](../dotnet/queue-front-stl-clr.md)|Accède au premier élément.|  
|[queue::get_container (STL/CLR)](../dotnet/queue-get-container-stl-clr.md)|Accède au conteneur sous-jacent.|  
|[queue::pop (STL/CLR)](../dotnet/queue-pop-stl-clr.md)|Supprime le premier élément.|  
|[queue::push (STL/CLR)](../dotnet/queue-push-stl-clr.md)|Ajoute un nouvel élément en dernier.|  
|[queue::queue (STL/CLR)](../dotnet/queue-queue-stl-clr.md)|Construit un objet conteneur.|  
|[queue::size (STL/CLR)](../dotnet/queue-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[queue::to_array (STL/CLR)](../dotnet/queue-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[queue::back_item (STL/CLR)](../dotnet/queue-back-item-stl-clr.md)|Accède au dernier élément.|  
|[queue::front_item (STL/CLR)](../dotnet/queue-front-item-stl-clr.md)|Accède au premier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator!= (queue) (STL/CLR)](../dotnet/operator-inequality-queue-stl-clr.md)|Détermine si un `queue` objet n’est pas égal à un autre `queue` objet.|  
|[operator< (queue) (STL/CLR)](../dotnet/operator-less-than-queue-stl-clr.md)|Détermine si un `queue` objet est inférieur à un autre `queue` objet.|  
|[operator<= (queue) (STL/CLR)](../dotnet/operator-less-or-equal-queue-stl-clr.md)|Détermine si un `queue` objet est inférieur ou égal à un autre `queue` objet.|  
|[operator== (queue) (STL/CLR)](../dotnet/operator-equality-queue-stl-clr.md)|Détermine si un `queue` objet est égal à un autre `queue` objet.|  
|[operator> (queue) (STL/CLR)](../dotnet/operator-greater-than-queue-stl-clr.md)|Détermine si un `queue` objet est supérieur à un autre `queue` objet.|  
|[operator>= (queue) (STL/CLR)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)|Détermine si un `queue` objet est supérieur ou égal à un autre `queue` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|IErreur\<valeur, le conteneur >|Mettre à jour la carte de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type `Container`, qui stocke `Value` éléments et à la demande. L’objet restreint l’accès au fait d’appuyer uniquement le premier élément et dépilé le dernier élément, en implémentant un premier sorti file d’attente (également appelé une file d’attente FIFO, ou simplement une file d’attente).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [pile (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
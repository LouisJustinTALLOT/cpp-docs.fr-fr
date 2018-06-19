---
title: pile (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack
dev_langs:
- C++
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 290857b51fea6726ec7e4a836d4afe1b33a8e615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172442"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)
La classe de modèle décrit un objet qui contrôle une séquence à longueur variable d’éléments qui dispose d’un accès dernier sorti. Utilisation de l’adaptateur de conteneur `stack` pour gérer un conteneur sous-jacent comme une pile de transmission de type push.  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`. De même, `GContainer` est identique à `Container` , sauf si ce dernier est un type référence, auquel cas il est `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    ref class stack  
        :   public  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>  
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
|[stack::const_reference (STL/CLR)](../dotnet/stack-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[stack::container_type (STL/CLR)](../dotnet/stack-container-type-stl-clr.md)|Type du conteneur sous-jacent.|  
|[stack::difference_type (STL/CLR)](../dotnet/stack-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[stack::generic_container (STL/CLR)](../dotnet/stack-generic-container-stl-clr.md)|Le type de l’interface générique pour l’adaptateur de conteneur.|  
|[stack::generic_value (STL/CLR)](../dotnet/stack-generic-value-stl-clr.md)|Le type d’un élément de l’interface générique de l’adaptateur de conteneur.|  
|[stack::reference (STL/CLR)](../dotnet/stack-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[stack::value_type (STL/CLR)](../dotnet/stack-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[stack::assign (STL/CLR)](../dotnet/stack-assign-stl-clr.md)|Remplace tous les éléments.|  
|[stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[stack::get_container (STL/CLR)](../dotnet/stack-get-container-stl-clr.md)|Accède au conteneur sous-jacent.|  
|[stack::pop (STL/CLR)](../dotnet/stack-pop-stl-clr.md)|Supprime le dernier élément.|  
|[stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)|Ajoute un nouvel élément en dernier.|  
|[stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[stack::stack (STL/CLR)](../dotnet/stack-stack-stl-clr.md)|Construit un objet conteneur.|  
|[stack::top (STL/CLR)](../dotnet/stack-top-stl-clr.md)|Accède au dernier élément.|  
|[stack::to_array (STL/CLR)](../dotnet/stack-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[stack::top_item (STL/CLR)](../dotnet/stack-top-item-stl-clr.md)|Accède au dernier élément.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
|[operator!= (stack) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)|Détermine si un `stack` objet n’est pas égal à un autre `stack` objet.|  
|[operator< (stack) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)|Détermine si un `stack` objet est inférieur à un autre `stack` objet.|  
|[operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)|Détermine si un `stack` objet est inférieur ou égal à un autre `stack` objet.|  
|[operator== (stack) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)|Détermine si un `stack` objet est égal à un autre `stack` objet.|  
|[operator> (stack) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)|Détermine si un `stack` objet est supérieur à un autre `stack` objet.|  
|[operator>= (stack) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)|Détermine si un `stack` objet est supérieur ou égal à un autre `stack` objet.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|IStack\<valeur, le conteneur >|Mettre à jour la carte de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type `Container`, qui stocke `Value` éléments et à la demande. L’objet limite l’accès en exécutant un push et POP simplement le dernier élément, mise en œuvre d’une file d’attente dernier sorti (également appelé une file d’attente LIFO ou pile).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/stack >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [liste (STL/CLR)](../dotnet/list-stl-clr.md)   
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
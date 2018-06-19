---
title: priority_queue (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::priority_queue
dev_langs:
- C++
helpviewer_keywords:
- priority_queue class [STL/CLR]
- <queue> header [STL/CLR]
- <cliext/queue> header [STL/CLR]
ms.assetid: 4d0000d3-68ff-4c4b-8157-7060540136f5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 63e806603a795a71dc2afb95ae17779d1c6f210b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172538"
---
# <a name="priorityqueue-stlclr"></a>priority_queue (STL/CLR)
La classe de modèle décrit un objet qui contrôle une longueur variable ordonné séquence d’éléments qui a un accès limité. Utilisation de l’adaptateur de conteneur `priority_queue` pour gérer un conteneur sous-jacent comme une file d’attente de priorité.  
  
 Dans la description ci-dessous, `GValue` est identique à `Value` , sauf si ce dernier est un type référence, auquel cas il est `Value^`. De même, `GContainer` est identique à `Container` , sauf si ce dernier est un type référence, auquel cas il est `Container^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Value,  
    typename Container>  
    ref class priority_queue  
        System::ICloneable,  
        Microsoft::VisualC::StlClr::IPriorityQueue<GValue, GContainer>  
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
|[priority_queue::const_reference (STL/CLR)](../dotnet/priority-queue-const-reference-stl-clr.md)|Type d'une référence constante à un élément.|  
|[priority_queue::container_type (STL/CLR)](../dotnet/priority-queue-container-type-stl-clr.md)|Type du conteneur sous-jacent.|  
|[priority_queue::difference_type (STL/CLR)](../dotnet/priority-queue-difference-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[priority_queue::generic_container (STL/CLR)](../dotnet/priority-queue-generic-container-stl-clr.md)|Le type de l’interface générique pour l’adaptateur de conteneur.|  
|[priority_queue::generic_value (STL/CLR)](../dotnet/priority-queue-generic-value-stl-clr.md)|Le type d’un élément de l’interface générique de l’adaptateur de conteneur.|  
|[priority_queue::reference (STL/CLR)](../dotnet/priority-queue-reference-stl-clr.md)|Type d'une référence à un élément.|  
|[priority_queue::size_type (STL/CLR)](../dotnet/priority-queue-size-type-stl-clr.md)|Type d'une distance signée entre deux éléments.|  
|[priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md)|Délégué de classement pour les deux éléments.|  
|[priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md)|Type d’un élément.|  
  
|Fonction membre|Description|  
|---------------------|-----------------|  
|[priority_queue::assign (STL/CLR)](../dotnet/priority-queue-assign-stl-clr.md)|Remplace tous les éléments.|  
|[priority_queue::empty (STL/CLR)](../dotnet/priority-queue-empty-stl-clr.md)|Vérifie l'absence d'éléments.|  
|[priority_queue::get_container (STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)|Accède au conteneur sous-jacent.|  
|[priority_queue::pop (STL/CLR)](../dotnet/priority-queue-pop-stl-clr.md)|Supprime l’élément de priorité hghest.|  
|[priority_queue::priority_queue (STL/CLR)](../dotnet/priority-queue-priority-queue-stl-clr.md)|Construit un objet conteneur.|  
|[priority_queue::push (STL/CLR)](../dotnet/priority-queue-push-stl-clr.md)|Ajoute un nouvel élément.|  
|[priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)|Compte le nombre d'éléments.|  
|[priority_queue::top (STL/CLR)](../dotnet/priority-queue-top-stl-clr.md)|Accède à l’élément de priorité la plus élevée.|  
|[priority_queue::to_array (STL/CLR)](../dotnet/priority-queue-to-array-stl-clr.md)|Copie de la séquence contrôlée vers un nouveau tableau.|  
|[priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)|Copie le délégué de classement pour les deux éléments.|  
  
|Propriété|Description|  
|--------------|-----------------|  
|[priority_queue::top_item (STL/CLR)](../dotnet/priority-queue-top-item-stl-clr.md)|Accède à l’élément de priorité la plus élevée.|  
  
|Opérateur|Description|  
|--------------|-----------------|  
|[priority_queue::operator= (STL/CLR)](../dotnet/priority-queue-operator-assign-stl-clr.md)|Remplace la séquence contrôlée.|  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Dupliquer un objet.|  
|IPriorityQueue\<valeur, le conteneur >|Mettre à jour la carte de conteneur générique.|  
  
## <a name="remarks"></a>Notes  
 L’objet alloue et libère du stockage pour la séquence qu’il contrôle via un conteneur sous-jacent, de type `Container`, qui stocke `Value` éléments et à la demande. Il conserve la séquence ordonnée en tant que segment, avec l’élément de priorité la plus élevée (l’élément supérieur) facilement accessible et amovible. L’objet limite l’accès en exécutant un push de nouveaux éléments et dépilé simplement l’élément de priorité la plus élevée, mise en œuvre d’une file d’attente de priorité.  
  
 L’objet ordonne la séquence qu’il contrôle en appelant un objet délégué stocké de type [priority_queue::value_compare (STL/CLR)](../dotnet/priority-queue-value-compare-stl-clr.md). Vous pouvez spécifier l’objet délégué stockées lorsque vous construisez le priority_queue ; Si vous ne spécifiez aucun objet délégué, la valeur par défaut est la comparaison `operator<(value_type, value_type)`. Pour accéder à cet objet stocké en appelant la fonction membre [priority_queue::value_comp (STL/CLR)](../dotnet/priority-queue-value-comp-stl-clr.md)`()`.  
  
 Cet objet de délégué doit imposer un classement faible strict sur les valeurs de type [priority_queue::value_type (STL/CLR)](../dotnet/priority-queue-value-type-stl-clr.md). Cela signifie que, pour toutes les deux clés `X` et `Y`:  
  
 `value_comp()(X, Y)` Retourne la valeur booléenne même résultat à chaque appel.  
  
 Si `value_comp()(X, Y)` est true, puis `value_comp()(Y, X)` doit avoir la valeur false.  
  
 Si `value_comp()(X, Y)` est true, puis `X` on dit d’être classé avant `Y`.  
  
 Si `!value_comp()(X, Y) && !value_comp()(Y, X)` est true, puis `X` et `Y` sont considérés comme ayant un classement équivalent.  
  
 Pour tout élément `X` qui précède `Y` dans la séquence contrôlée, `key_comp()(Y, X)` a la valeur false. (Pour l’objet de délégué par défaut, les clés jamais diminuent dans valeur.)  
  
 L’élément de priorité la plus élevée est donc un des éléments qui n’est pas classé avant tout autre élément.  
  
 Étant donné que le conteneur sous-jacent conserve des éléments classés comme un segment de mémoire :  
  
 Le conteneur doit prendre en charge des itérateurs d’accès aléatoire.  
  
 Éléments avec un classement équivalent peuvent être dépilés dans un ordre différent, qu’elles ont été appliquées. (L’ordre n’est pas stable.)  
  
 Par conséquent, incluent des candidats pour le conteneur sous-jacent [deque (STL/CLR)](../dotnet/deque-stl-clr.md) et [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/file d’attente >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [file d’attente (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [pile (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [vecteur (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)
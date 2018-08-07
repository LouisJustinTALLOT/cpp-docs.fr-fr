---
title: Eventtargetarray::eventtargetarray, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 831c9a524f8120c855382d198a5f53ac312cada6
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569786"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray, constructeur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *ressources humaines*  
 Après les opérations de ce constructeur, paramètre *hr* indique si l’allocation du tableau a réussi ou échoué. Le tableau suivant répertorie les valeurs possibles pour *hr*.  
  
 S_OK  
 L’opération a réussi.  
  
 E_OUTOFMEMORY  
 N’a pas pu allouer la mémoire pour le tableau.  
  
 S_FALSE  
 Paramètre *éléments* est inférieure ou égale à zéro.  
  
 *éléments*  
 Le nombre d’éléments de tableau à allouer.  
  
## <a name="remarks"></a>Notes  
 Initialise une nouvelle instance de la **EventTargetArray** classe.  
  
 **EventTargetArray** permet de garder un tableau des gestionnaires d’événements dans un `EventSource` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Eventtargetarray, classe](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
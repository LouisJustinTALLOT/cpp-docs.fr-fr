---
title: Eventtargetarray::eventtargetarray, constructeur | Documents Microsoft
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
ms.openlocfilehash: fbfd12ea513044f1062e60f5c73f5089683f043d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872713"
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
  
#### <a name="parameters"></a>Paramètres  
 `hr`  
 Après les opérations de ce constructeur, paramètre `hr` indique si l’allocation du tableau a réussi ou échoué. Le tableau suivant répertorie les valeurs possibles pour `hr`.  
  
 S_OK  
 L’opération a réussi.  
  
 E_OUTOFMEMORY  
 Impossible d’allouer la mémoire pour le tableau.  
  
 S_FALSE  
 Paramètre `items` est inférieur ou égal à zéro.  
  
 `items`  
 Le nombre d’éléments de tableau à allouer.  
  
## <a name="remarks"></a>Notes  
 Initialise une nouvelle instance de la classe EventTargetArray.  
  
 EventTargetArray est utilisé pour conserver un tableau de gestionnaires d’événements dans un objet source d’événement.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [EventTargetArray (classe)](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
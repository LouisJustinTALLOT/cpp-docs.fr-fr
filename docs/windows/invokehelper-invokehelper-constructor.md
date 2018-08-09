---
title: InvokeHelper::InvokeHelper, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
dev_langs:
- C++
helpviewer_keywords:
- InvokeHelper, constructor
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 75ad1b82d6d4a28db94ef00a234547091969722b
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020025"
---
# <a name="invokehelperinvokehelper-constructor"></a>InvokeHelper::InvokeHelper, constructeur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
explicit InvokeHelper(  
   TCallback callback  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *rappel*  
 Un gestionnaire d’événements.  
  
## <a name="remarks"></a>Notes  
 Initialise une nouvelle instance de la **InvokeHelper** classe.  
  
 Le `TCallback` paramètre de modèle spécifie le type du Gestionnaire d’événements.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** event.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [InvokeHelper (Structure)](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
---
title: Chaininterfaces::iidcount, constante | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs:
- C++
helpviewer_keywords:
- IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6d089e9639d83150e501b32577de94fc43b516c1
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463939"
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount, constante
Le nombre total d’ID contenues dans les interfaces spécifiées par les paramètres de modèle d’interface *I0* via *I9*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le nombre total de l’ID d’interface.  
  
## <a name="remarks"></a>Notes  
 Paramètres de modèle *I0* et *I1* sont nécessaires et les paramètres *I2* via *I9* sont facultatifs. Le nombre de l’IID de chaque interface est généralement de 1.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ChainInterfaces, structure](../windows/chaininterfaces-structure.md)
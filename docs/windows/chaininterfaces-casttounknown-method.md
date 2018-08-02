---
title: Chaininterfaces::casttounknown, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: a6a58555-e5b0-4773-aba0-959d9d362c6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9479180134e8a873e1d79f91deb3d29700d40a2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467168"
---
# <a name="chaininterfacescasttounknown-method"></a>ChainInterfaces::CastToUnknown, méthode
Convertit le pointeur d’interface du type défini par le *I0* paramètre de modèle à un pointeur IUnknown.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’interface IUnknown.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ChainInterfaces, structure](../windows/chaininterfaces-structure.md)
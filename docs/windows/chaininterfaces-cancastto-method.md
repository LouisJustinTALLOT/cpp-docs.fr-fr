---
title: Chaininterfaces::cancastto, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: 8be44875-53ed-494b-91a0-0f8e399685bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5839edd90f61f9f4aa96ea1d921d2179660be554
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461208"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo, méthode
Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par les paramètres du modèle de celle par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *riid*  
 ID d’interface.  
  
 *PPV*  
 Pointeur vers le dernier ID d’interface qui a été converti avec succès.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si toutes les opérations de cast a réussi ; sinon, **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ChainInterfaces, structure](../windows/chaininterfaces-structure.md)
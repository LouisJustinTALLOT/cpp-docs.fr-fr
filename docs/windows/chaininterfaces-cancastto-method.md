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
ms.openlocfilehash: ff24ac92e5e84cb85127ef6e33805928fabd6f60
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647529"
---
# <a name="chaininterfacescancastto-method"></a>ChainInterfaces::CanCastTo, méthode
Indique si l’ID d’interface spécifié peut être casté à chacune des spécialisations définies par les paramètres du modèle de celle par défaut.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline bool CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Paramètres  
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
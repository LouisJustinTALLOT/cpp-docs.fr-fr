---
title: Chaininterfaces::cancastto, méthode | Documents Microsoft
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
ms.openlocfilehash: c2286c347fbd68f34fac807e80facca0a0286aa6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860292"
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
 `riid`  
 ID d’interface.  
  
 `ppv`  
 Pointeur vers le dernier ID d’interface qui a été effectué avec succès.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si toutes les opérations de cast a réussi ; dans le cas contraire, `false`.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ChainInterfaces, structure](../windows/chaininterfaces-structure.md)
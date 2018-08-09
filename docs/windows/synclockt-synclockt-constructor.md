---
title: Synclockt::synclockt, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceaafd6230e6497ed2b7636ad5070141546cb8d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648163"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT, constructeur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *other*  
 Une référence rvalue à un autre **SyncLockT** objet.  
  
 *sync*  
 Une référence à un autre `SyncLockWithStatusT` objet.  
  
## <a name="remarks"></a>Notes  
 Initialise une nouvelle instance de la **SyncLockT** classe.  
  
 Le premier constructeur initialise actuel **SyncLockT** objet à partir d’un autre **SyncLockT** objet spécifié par le paramètre *autres*et puis invalide l’autres  **SyncLockT** objet. Le deuxième constructeur est **protégé**et l’initialise actuel **SyncLockT** objet à un état non valide.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [SyncLockT, classe](../windows/synclockt-class.md)
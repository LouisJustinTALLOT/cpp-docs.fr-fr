---
title: Synclockt::synclockt, constructeur | Documents Microsoft
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
ms.openlocfilehash: c3353df1a73821a2009aeba2367f1892b06aba5b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889837"
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
  
#### <a name="parameters"></a>Paramètres  
 `other`  
 Une référence rvalue à un autre objet SyncLockT.  
  
 `sync`  
 Une référence à un autre objet SyncLockWithStatusT.  
  
## <a name="remarks"></a>Notes  
 Initialise une nouvelle instance de la classe SyncLockT.  
  
 Le premier constructeur initialise l’objet SyncLockT actuel à partir d’un autre objet SyncLockT spécifié par le paramètre `other`et puis invalide l’autre objet SyncLockT. Le deuxième constructeur est `protected`et initialise l’objet SyncLockT actuel à un état non valide.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [SyncLockT, classe](../windows/synclockt-class.md)
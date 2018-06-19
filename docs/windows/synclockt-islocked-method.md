---
title: Synclockt::IsLocked, méthode | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 067b3763e10b2bbb310b213f7d748e953ba2a902
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888473"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool IsLocked() const;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si l’objet SyncLockT est verrouillée ; sinon, **false**.  
  
## <a name="remarks"></a>Notes  
 Indique si l’objet SyncLockT actuel possède une ressource ; l’objet SyncLockT est *verrouillé*.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [SyncLockT, classe](../windows/synclockt-class.md)
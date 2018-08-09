---
title: Synclockwithstatust::IsLocked, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 80c744431fe7df32be705fcf91eef0a8691b8fa4
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015796"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked, méthode
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
bool IsLocked() const;  
```  
  
## <a name="remarks"></a>Notes  
 Indique si l’actuel **SyncLockWithStatusT** objet possède une ressource, c'est-à-dire, le **SyncLockWithStatusT** objet est *verrouillé*.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le **SyncLockWithStatusT** objet est verrouillé ; sinon, **false**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Voir aussi  
 [SyncLockWithStatusT, classe](../windows/synclockwithstatust-class.md)
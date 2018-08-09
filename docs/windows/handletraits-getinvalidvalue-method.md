---
title: Handletraits::getinvalidvalue, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- GetInvalidValue method
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4690daabd84b8127913af0a96d5b929ee986e77
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651231"
---
# <a name="handletraitsgetinvalidvalue-method"></a>HANDLETraits::GetInvalidValue, méthode
Représente un handle non valide.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline static HANDLE GetInvalidValue();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours INVALID_HANDLE_VALUE. (INVALID_HANDLE_VALUE est défini par Windows.)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>Voir aussi  
 [HANDLETraits, structure](../windows/handletraits-structure.md)
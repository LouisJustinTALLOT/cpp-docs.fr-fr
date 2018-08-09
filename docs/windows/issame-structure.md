---
title: IsSame (Structure) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
dev_langs:
- C++
helpviewer_keywords:
- IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b63e3784529edf8957654511af53373fd80799ae
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014258"
---
# <a name="issame-structure"></a>IsSame (structure)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template <  
   typename T1,  
   typename T2  
>  
struct IsSame;  
template <  
   typename T1  
>  
struct IsSame<T1, T1>;  
```  
  
### <a name="parameters"></a>Paramètres  
 *T1*  
 Type.  
  
 *T2*  
 Un autre type.  
  
## <a name="remarks"></a>Notes  
 Teste si un spécifié le type est identique à un autre de type spécifié.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constants"></a>Constantes publiques  
  
|Name|Description|  
|----------|-----------------|  
|[IsSame::value, constante](../windows/issame-value-constant.md)|Indique si un type est identique à un autre.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IsSame`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** internal.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
---
title: Asyncresulttype, énumération | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
dev_langs:
- C++
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8171c4a57621a4f17a5f0ddb0745faa70fde6524
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465283"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType (énumération)
Spécifie le type de résultat retourné par la `GetResults()` (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum AsyncResultType;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="values"></a>Valeurs  
  
|Nom|Description|  
|----------|-----------------|  
|`MultipleResults`|Un ensemble de résultats multiples, qui sont présentées progressivement entre `Start` état et avant `Close()` est appelée.|  
|`SingleResult`|Un résultat unique, qui est présenté après la survenue de l’événement Complete.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)
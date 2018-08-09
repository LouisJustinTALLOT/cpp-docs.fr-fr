---
title: Asyncbase::ErrorCode, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a5f4ccbe1789914f5a7c378f5cb847aaa1c49bb8
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644701"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode, méthode
Récupère le code d’erreur pour l’opération asynchrone actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *Erreur*  
 L’emplacement où cette opération stocke le code d’erreur actuel.  
  
## <a name="remarks"></a>Notes  
 Cette opération est thread-safe.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)
---
title: Asyncbase::ErrorCode, méthode | Documents Microsoft
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
ms.openlocfilehash: abd3eae18d793739866b6c0dd8a1b6a994093c93
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859577"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode, méthode
Récupère le code d’erreur pour l’opération asynchrone actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `error`  
 L’emplacement où cette opération stocke le code d’erreur actuel.  
  
## <a name="remarks"></a>Notes  
 Cette opération est thread-safe.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** async.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [AsyncBase, classe](../windows/asyncbase-class.md)
---
title: Mutex::mutex, constructeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d87c07f7fa4f1dfa6cbb34545d74d75e8a867583
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017082"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex, constructeur
Initialise une nouvelle instance de la **Mutex** classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
### <a name="parameters"></a>Paramètres  
 *h*  
 Un handle ou une référence rvalue à un handle, pour un **Mutex** objet.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un **Mutex** objet à partir du handle spécifié. Le deuxième constructeur initialise un **Mutex** objet à partir du handle spécifié, puis passe la propriété du mutex actuel **Mutex** objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>Voir aussi
 [Mutex (classe)](../windows/mutex-class1.md)
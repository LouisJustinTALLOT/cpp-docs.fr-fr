---
title: Mutex::mutex, constructeur | Documents Microsoft
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
ms.openlocfilehash: bb7782e44fc8598ca3b806ef922f8d0840765e28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876454"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex, constructeur
Initialise une nouvelle instance de la classe Mutex.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
explicit Mutex(  
   HANDLE h  
);  
  
Mutex(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `h`  
 Un handle ou une référence rvalue à un handle, à un objet Mutex.  
  
## <a name="remarks"></a>Notes  
 Le premier constructeur initialise un objet Mutex à partir du handle spécifié. Le deuxième constructeur initialise un objet Mutex à partir du handle spécifié et la propriété du mutex est alors transférée vers l’objet Mutex actuel.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>Voir aussi
 [Mutex (classe)](../windows/mutex-class1.md)
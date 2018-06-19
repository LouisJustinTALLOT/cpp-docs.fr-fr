---
title: Mutex::operator =, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9b0ee206-a930-4fea-8dc0-1f79839e9d13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8791d3c947206be399f475bb8c895b2b5e032133
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875485"
---
# <a name="mutexoperator-operator"></a>Mutex::operator=, opérateur
Affecte (se déplace) le Mutex spécifié de l’objet à l’objet Mutex actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mutex& operator=(  
   _Inout_ Mutex&& h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `h`  
 Une référence rvalue à un objet Mutex.  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence à l’objet Mutex actuel.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez la **sémantique de déplacement** section de [déclarateur de référence Rvalue : & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>Voir aussi
 [Mutex (classe)](../windows/mutex-class1.md)
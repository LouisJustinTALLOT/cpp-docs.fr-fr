---
title: Semaphore::operator =, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Semaphore::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: ea19839f-91f0-4b00-a35b-5728fcba4981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25287e642bd368470b207ed237f44ca70773064e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892525"
---
# <a name="semaphoreoperator-operator"></a>Semaphore::operator=, opérateur
Déplace le handle spécifié à partir d’un objet sémaphore à l’objet de sémaphore actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Semaphore& operator=(  
   _Inout_ Semaphore&& h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `h`  
 Référence rvalue à un objet de sémaphore.  
  
## <a name="return-value"></a>Valeur de retour  
 Une référence à l’objet de sémaphore actuel.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers
 
 ## <a name="see-also"></a>Voir aussi
 [Semaphore, classe](../windows/semaphore-class.md)
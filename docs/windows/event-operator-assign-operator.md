---
title: Event::operator =, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d3da41ff7fd145889ec799bb2f8ebe99aed36934
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871121"
---
# <a name="eventoperator-operator"></a>Event::operator=, opérateur
Assigne la référence Event spécifiée à l'instance Event actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `h`  
 Une référence rvalue à une instance de l’événement.  
  
## <a name="return-value"></a>Valeur de retour  
 Pointeur vers l’instance Event actuelle.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** corewrappers.h  
  
 **Namespace :** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>Voir aussi  
 [Event, classe (bibliothèque de modèles Windows Runtime C++)](../windows/event-class-windows-runtime-cpp-template-library.md)
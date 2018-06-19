---
title: RaiseException (fonction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
dev_langs:
- C++
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2af97ac13386db450318f4d1f384517a8dd77baf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882181"
---
# <a name="raiseexception-function"></a>RaiseException (fonction)
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline void __declspec(noreturn)   RaiseException(  
      HRESULT hr,   
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hr`  
 Le code d’exception de l’exception est levée ; Autrement dit, la valeur HRESULT d’échec d’une opération.  
  
 `dwExceptionFlags`  
 Un indicateur qui indique une exception non bloquantes (la valeur de l’indicateur est égal à zéro), ou une exception noncontinuable (la valeur de l’indicateur est différente de zéro). Par défaut, l’exception est qui empêchait celle-ci.  
  
## <a name="remarks"></a>Notes  
 Lève une exception dans le thread appelant.  
  
 Pour plus d’informations, consultez les fenêtres **RaiseException** (fonction).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** internal.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
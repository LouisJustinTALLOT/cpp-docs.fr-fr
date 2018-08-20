---
title: DeferrableEventArgs::InvokeAllFinished (méthode) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883366"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished (méthode)
Appelé pour indiquer que le traitement d'un événement différé est terminé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>Notes  
 Vous devez appeler cette méthode après les appels de source d’événement [InvokeAll](../windows/eventsource-invokeall-method.md). L'appel à cette méthode empêche tout autre report et force l'exécution du gestionnaire d'achèvement en l'absence de report.  
  
 Pour obtenir un exemple de code, consultez [deferrableeventargs, classe](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** event.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [Deferrableeventargs, classe](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll, méthode](../windows/eventsource-invokeall-method.md)
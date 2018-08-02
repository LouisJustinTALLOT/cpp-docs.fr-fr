---
title: ComPtrRef::operator InterfaceType**, opérateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
dev_langs:
- C++
helpviewer_keywords:
- operator InterfaceType** operator
ms.assetid: b32e3240-a4f0-4998-a55f-d4e35dc9a15a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6401d78f0c410057d41a80f2345255d4876adb23
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464413"
---
# <a name="comptrrefoperator-interfacetype-operator"></a>ComPtrRef::operator InterfaceType**, opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator InterfaceType**();  
```  
  
## <a name="remarks"></a>Notes  
 Supprime l’actuel **ComPtrRef** de l’objet et retourne un pointeur-à-un-pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtrRef (classe)](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
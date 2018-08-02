---
title: ComPtrRef::operator void **, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
dev_langs:
- C++
helpviewer_keywords:
- operator void** operator
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bbe9f077fd0d80a831d319660be26090ad5411f6
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463851"
---
# <a name="comptrrefoperator-void-operator"></a>ComPtrRef::operator void\* \* opérateur
Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
operator void**() const;  
```  
  
## <a name="remarks"></a>Notes  
 Supprime actuel **ComPtrRef** d’objet, convertit le pointeur vers l’interface qui a été représenté par le **ComPtrRef** objet sous la forme d’un pointeur à pointeur-à **void**, puis Retourne le pointeur de cast.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Namespace :** Microsoft::WRL::Details  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtrRef (classe)](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)
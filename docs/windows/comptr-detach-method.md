---
title: Comptr::Detach, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abc30204969464323d4995310cee0866139734fc
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648007"
---
# <a name="comptrdetach-method"></a>ComPtr::Detach, méthode
Il dissocie **ComPtr** objet à partir de l’interface qu’elle représente.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
T* Detach();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Un pointeur vers l’interface qui a été représenté par cet **ComPtr** objet.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr, classe](../windows/comptr-class.md)
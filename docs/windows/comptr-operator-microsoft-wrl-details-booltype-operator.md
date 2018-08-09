---
title: ComPtr::operator Microsoft::WRL::Details::BoolType opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb5735eeb9cd4048596588765468fbb9c5e07496
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652599"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur
Indique ou non un **ComPtr** gère la durée de vie d’une interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Si une interface est associée à ce **ComPtr**, l’adresse de la [BoolStruct::Member](../windows/boolstruct-member-data-member.md) membre de données ; sinon, **nullptr**.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** client.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ComPtr (classe)](../windows/comptr-class.md)   
 [ComPtr::Get, méthode](../windows/comptr-get-method.md)
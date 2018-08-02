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
ms.openlocfilehash: 1a4ec737c3f24899e50220c3e862283b88a826b9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461162"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType, opérateur
Indique ou non un **ComPtr** gère la durée de vie d’une interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
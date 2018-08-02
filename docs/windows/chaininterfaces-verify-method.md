---
title: Chaininterfaces::Verify, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a845ea047682fda97ae581f4daad26775241ddf8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466837"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify, méthode
Vérifie que chaque interface définie par les paramètres de modèle *I0* via *I9* hérite d’IUnknown et/ou IInspectable et qui *I0* hérite *I1* via *I9*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Notes  
 Si l’opération de vérification échoue, un **static_assert** émet un message d’erreur qui décrit l’échec.  
  
## <a name="remarks"></a>Notes  
 Paramètres de modèle *I0* et *I1* sont nécessaires et les paramètres *I2* via *I9* sont facultatifs.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ChainInterfaces, structure](../windows/chaininterfaces-structure.md)
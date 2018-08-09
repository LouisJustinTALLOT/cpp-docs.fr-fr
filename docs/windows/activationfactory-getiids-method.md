---
title: Activationfactory::getiids, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetIids
dev_langs:
- C++
helpviewer_keywords:
- GetIids method
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aaaa8d5bb0a88b9078c60fa61608e52fafd5baac
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643509"
---
# <a name="activationfactorygetiids-method"></a>ActivationFactory::GetIids, méthode
Récupère un tableau d’ID d’interface implémentée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
### <a name="parameters"></a>Paramètres  
 *iidCount*  
 Lorsque cette opération se termine, le nombre d’ID interface dans le *IID* tableau.  
  
 *IID*  
 Lorsque cette opération est terminée, un tableau d’implémenté des ID d’interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de succès. Sinon, valeur HRESULT qui décrit l’erreur. E_OUTOFMEMORY est un HRESULT d’échec possible.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ActivationFactory, classe](../windows/activationfactory-class.md)
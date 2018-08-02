---
title: Activationfactory::gettrustlevel, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: af3ec58afd69f3fde6e2eb67969f1dad8848c5de
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466720"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel, méthode
Obtient le niveau de confiance de l’objet qui actuel **ActivationFactory** instancie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *trustLvl*  
 Lorsque cette opération est terminée, le niveau de confiance du runtime de classe qui le **ActivationFactory** instancie.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK en cas de réussite ; Sinon, une erreur d’assertion est émise et *trustLvl* est défini sur FullTrust.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** module.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [ActivationFactory, classe](../windows/activationfactory-class.md)
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
ms.openlocfilehash: eba02bea09784e3431b3697eb9ac9a47de978348
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424558"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel, méthode

Obtient le niveau de confiance de l’objet qui actuel **ActivationFactory** instancie.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Paramètres

*trustLvl*<br/>
Lorsque cette opération est terminée, le niveau de confiance du runtime de classe qui le **ActivationFactory** instancie.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur d’assertion est émise et *trustLvl* est défini sur `FullTrust`.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[ActivationFactory, classe](../windows/activationfactory-class.md)
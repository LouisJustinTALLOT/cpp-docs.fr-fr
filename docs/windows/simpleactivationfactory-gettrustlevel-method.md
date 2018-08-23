---
title: Simpleactivationfactory::gettrustlevel, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5a1838c153dc7a0a4def9f98e5e043e36ae9414
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603843"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel, méthode

Obtient le niveau de confiance d’une instance de la classe spécifiée par le `Base` paramètre de modèle de classe.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Paramètres

*trustLvl*  
Lorsque cette opération se termine, le niveau de confiance de l’objet de classe actuel.

## <a name="return-value"></a>Valeur de retour

Toujours S_OK.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[SimpleActivationFactory, classe](../windows/simpleactivationfactory-class.md)
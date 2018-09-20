---
title: Module::registerwinrtobject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- RegisterWinRTObject method
ms.assetid: a2782c9c-b9c5-4e4b-9c8d-ef513aea20c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 496b1ccac5b998ba08f4e2eccfe31ffd18f2c37d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431786"
---
# <a name="moduleregisterwinrtobject-method"></a>Module::RegisterWinRTObject, méthode

Inscrit un ou plusieurs objets Windows Runtime pour d’autres applications peuvent se connecter à leur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)  
```

### <a name="parameters"></a>Paramètres

*Nom du serveur*<br/>
Nom qui spécifie un sous-ensemble d’objets affectés par cette opération.

*activatableClassIds*<br/>
Tableau des CLSID activables à inscrire.

*Cookie*<br/>
Une valeur qui identifie les objets de classe qui ont été inscrits. Cette valeur est utilisée ultérieurement pour révoquer l’inscription.

*count*<br/>
Le nombre d’objets à inscrire.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)
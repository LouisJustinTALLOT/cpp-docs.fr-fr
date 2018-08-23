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
ms.openlocfilehash: a7f5879a3a76e9af795a5dfc808423b43515662a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609299"
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

*Nom du serveur*  
Nom qui spécifie un sous-ensemble d’objets affectés par cette opération.

*activatableClassIds*  
Tableau des CLSID activables à inscrire.

*Cookie*  
Une valeur qui identifie les objets de classe qui ont été inscrits. Cette valeur est utilisée ultérieurement pour révoquer l’inscription.

*count*  
Le nombre d’objets à inscrire.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT comme CO_E_OBJISREG qui indique la raison pour laquelle l’opération a échoué.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi
[Module, classe](../windows/module-class.md)
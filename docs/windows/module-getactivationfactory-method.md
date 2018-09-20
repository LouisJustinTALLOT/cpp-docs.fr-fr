---
title: Module::getactivationfactory, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory method
ms.assetid: 59da8844-072e-414b-b89c-1db1cc4fd81d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 995594ee48e6ca408e88d9ab14968d88b536d309
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403505"
---
# <a name="modulegetactivationfactory-method"></a>Module::GetActivationFactory, méthode

Obtient une fabrique d’activation pour le module.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Paramètres

*pActivatibleClassId*<br/>
IID d’une classe runtime.

*ppIFactory*<br/>
IActivationFactory pour la classe runtime spécifié.

*Nom du serveur*<br/>
Le nom d’un sous-ensemble des fabriques de classes du module en cours. Spécifiez le nom du serveur utilisé dans le [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) (macro), ou spécifiez **nullptr** pour obtenir le nom du serveur par défaut.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, le HRESULT retourné par GetActivationFactory.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)<br/>
[ActivatableClass, macros](../windows/activatableclass-macros.md)
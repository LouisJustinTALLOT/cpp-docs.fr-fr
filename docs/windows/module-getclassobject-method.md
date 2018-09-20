---
title: Module::GetClassObject, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- GetClassObject method
ms.assetid: 95b0de1b-f728-4f96-9f44-f6ea71ce56e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 90a1b527d12e581c42fc9519e56d453f845e0b63
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419715"
---
# <a name="modulegetclassobject-method"></a>Module::GetClassObject, méthode

Récupère un cache des fabriques de classes.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
ID de classe.

*riid*<br/>
ID d’interface que vous demandez.

*PPV*<br/>
Pointeur vers l’objet retourné.

*Nom du serveur*<br/>
Le nom du serveur qui est spécifié dans le `ActivatableClassWithFactory`, `ActivatableClassWithFactoryEx`, ou `ActivatableClass` macro ; ou **nullptr** pour obtenir le nom du serveur par défaut.

## <a name="return-value"></a>Valeur de retour

## <a name="remarks"></a>Notes

Utilisez cette méthode uniquement pour COM, pas l’exécution de Windows. Cette méthode expose uniquement `IClassFactory` méthodes.

## <a name="requirements"></a>Configuration requise

**En-tête :** module.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Module, classe](../windows/module-class.md)
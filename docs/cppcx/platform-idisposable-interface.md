---
description: 'En savoir plus sur : interface Platform :: IDisposable'
title: Interface Platform::IDisposable
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: 0a1e7b44861d48f496f21d634d4d28ff1c968bcf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276775"
---
# <a name="platformidisposable-interface"></a>Interface Platform::IDisposable

Utilisée pour libérer des ressources non managées.

## <a name="syntax"></a>Syntaxe

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Attributs

**GuidAttribute**("de0cbaea-8065-4a45-B196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Membres

L’interface IDisposable hérite de l’interface IUnknown. IDisposable a également les types de membre suivants :

**Méthodes**

L’interface IDisposable possède les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|Dispose|Utilisée pour libérer des ressources non managées.|

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

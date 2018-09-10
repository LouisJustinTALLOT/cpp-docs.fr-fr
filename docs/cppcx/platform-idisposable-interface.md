---
title: Platform::IDisposable (Interface) | Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c596e4054729855ea3c8caedf632ca8dd50b796a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105066"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable (interface)

Utilisée pour libérer des ressources non managées.

## <a name="syntax"></a>Syntaxe

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Attributs

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Membres

L’interface IDisposable hérite de l’interface IUnknown. IDisposable a également les types de membre suivants :

**Méthodes**

L’interface IDisposable possède les méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|Suppression|Utilisée pour libérer des ressources non managées.|

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform
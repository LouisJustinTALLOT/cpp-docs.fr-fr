---
title: Platform::CallbackContext (énumération)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 7f4e020ab0b1e377456c27d3b4666e15b5a4f7a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161664"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext (énumération)

Spécifie le contexte de thread dans lequel s’exécute une fonction de rappel (Gestionnaire d’événements).

## <a name="syntax"></a>Syntaxe

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Membres

|Code de type|Description|
|---------------|-----------------|
|Any|La fonction de rappel peut s’exécuter sur n’importe quel contexte de thread.|
|Identique|La fonction de rappel peut s’exécuter uniquement sur le contexte de thread qui a démarré l’opération asynchrone.|

### <a name="requirements"></a>Configuration requise

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd
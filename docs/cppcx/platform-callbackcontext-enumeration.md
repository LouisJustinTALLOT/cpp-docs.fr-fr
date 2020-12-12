---
description: 'En savoir plus sur : Platform :: CallbackContext, énumération'
title: Platform::CallbackContext (énumération)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 36c30b674065f42f7d50a403d1506344ffcfecac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170969"
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
|Quelconque|La fonction de rappel peut s’exécuter sur n’importe quel contexte de thread.|
|Identique|La fonction de rappel peut s’exécuter uniquement sur le contexte de thread qui a démarré l’opération asynchrone.|

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

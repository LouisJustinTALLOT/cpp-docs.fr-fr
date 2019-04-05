---
title: Invokemodeoptions, Structure
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 0e5b45042c9959b87ad5db97ab755e49de469149
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035278"
---
# <a name="invokemodeoptions-structure"></a>Invokemodeoptions, Structure

Spécifie s’il faut déclencher tous les événements dans la file d’attente de délégué, ou arrêter le déclenchement d’après qu’une erreur est générée. Les valeurs autorisées sont spécifiés dans le `InvokeMode` enum.

## <a name="syntax"></a>Syntaxe

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>Configuration requise

**En-tête :** event.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[Classe de Microsoft::wrl::AgileEventSource](agileeventsource-class.md)
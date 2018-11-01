---
title: Invokemodeoptions, Structure
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 315f1f0c49c4222bf525bbaf25c9ad0de8b9c7d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511695"
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

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)<br/>
[Classe de Microsoft::wrl::AgileEventSource](../windows/agileeventsource-class.md)
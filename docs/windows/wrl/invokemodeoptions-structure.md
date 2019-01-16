---
title: Invokemodeoptions, Structure
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: ff16c6c5a2ce09313283198fe0b86e95d572e46c
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336065"
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

## <a name="requirements"></a>Spécifications

**En-tête :** event.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[Classe de Microsoft::wrl::AgileEventSource](agileeventsource-class.md)
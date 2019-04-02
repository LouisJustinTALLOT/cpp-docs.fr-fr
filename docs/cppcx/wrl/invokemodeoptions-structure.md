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
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784606"
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
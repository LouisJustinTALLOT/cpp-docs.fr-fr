---
title: InvokeModeOptions, structure
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 9bca49479d97ee371f6728f90a9aa96da0387f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213835"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions, structure

Spécifie s’il faut activer tous les événements dans la file d’attente du délégué, ou arrêter le déclenchement après qu’une erreur a été générée. Les valeurs autorisées sont spécifiées dans l’énumération `InvokeMode`.

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

**En-tête :** Event. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[Classe Microsoft :: WRL :: AgileEventSource](agileeventsource-class.md)

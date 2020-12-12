---
description: 'En savoir plus sur : structure InvokeModeOptions'
title: InvokeModeOptions, structure
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 1e1382242c95c47355239c220c43c278280dd451
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298979"
---
# <a name="invokemodeoptions-structure"></a>InvokeModeOptions, structure

Spécifie s’il faut activer tous les événements dans la file d’attente du délégué, ou arrêter le déclenchement après qu’une erreur a été générée. Les valeurs autorisées sont spécifiées dans l' `InvokeMode` énumération.

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

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)<br/>
[Classe Microsoft :: WRL :: AgileEventSource](agileeventsource-class.md)

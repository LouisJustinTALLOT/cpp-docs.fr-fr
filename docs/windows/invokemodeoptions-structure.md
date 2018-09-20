---
title: Invokemodeoptions, Structure | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ea549db29f7fcb67e4d59e341bf7d5ad085b6d7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392708"
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
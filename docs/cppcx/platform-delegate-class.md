---
title: Platform::Delegate (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 1b4a4955bbff53e6e0c5606f2900e22cc69146cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446226"
---
# <a name="platformdelegate-class"></a>Platform::Delegate (classe)

Représente un objet de fonction.

## <a name="syntax"></a>Syntaxe

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>Membres

La classe Delegate contient les méthodes Equals(), GetHashCode(), et ToString() dérivées de la [Platform::Object Class](../cppcx/platform-object-class.md).

### <a name="remarks"></a>Notes

Utilisez le mot clé [delegate](../windows/delegate-cpp-component-extensions.md) pour créer des délégués. N’utilisez pas Platform::Delegate explicitement. Pour plus d’informations, consultez [Délégués](../cppcx/delegates-c-cx.md). Pour obtenir un exemple montrant comment créer et consommer un délégué, consultez [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)
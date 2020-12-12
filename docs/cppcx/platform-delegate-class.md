---
description: 'En savoir plus sur : plateforme ::D classe délégué'
title: Platform::Delegate (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 58baedf595d3ee8d9cc4975e787193abf522233c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176104"
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

Utilisez le mot clé [delegate](../extensions/delegate-cpp-component-extensions.md) pour créer des délégués. N’utilisez pas Platform::Delegate explicitement. Pour plus d'informations, consultez [Délégués](../cppcx/delegates-c-cx.md). Pour obtenir un exemple montrant comment créer et consommer un délégué, consultez [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)

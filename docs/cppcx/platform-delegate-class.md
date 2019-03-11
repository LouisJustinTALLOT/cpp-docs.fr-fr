---
title: Platform::Delegate (classe)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 6a509827b3b8e14b6d28995b5b4ca468ee9a662e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741173"
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

### <a name="requirements"></a>Spécifications

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Espace de noms Platform](../cppcx/platform-namespace-c-cx.md)

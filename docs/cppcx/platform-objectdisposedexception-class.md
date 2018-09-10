---
title: Platform::ObjectDisposedException, classe | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ObjectDisposedException
- VCCORLIB/Platform::ObjectDisposedException::ObjectDisposedException
dev_langs:
- C++
helpviewer_keywords:
- Platform::ObjectDisposedException
ms.assetid: 68506fe4-d09c-4407-999f-1e3edb261d41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f0574885fb404572052fbf5066b522ed0208eba
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106923"
---
# <a name="platformobjectdisposedexception-class"></a>Platform::ObjectDisposedException, classe

Levée lorsqu'une opération est exécutée sur un objet supprimé.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class ObjectDisposedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez l'exception [COMException](../cppcx/platform-comexception-class.md).

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::COMException, classe](../cppcx/platform-comexception-class.md)
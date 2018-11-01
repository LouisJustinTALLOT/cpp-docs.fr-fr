---
title: Platform::FailureException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: b1890fb0649dee779b3851ed9f1fc46a67b2916d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472616"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException, classe

Levée lorsque l'opération a échoué. Il s'agit de l'équivalent de E_FAIL HRESULT.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez la classe [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Configuration requise

**Minimum de client pris en charge :** Windows 8

**Minimum de serveur pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::COMException, classe](../cppcx/platform-comexception-class.md)
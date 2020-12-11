---
description: 'En savoir plus sur : classe Platform :: FailureException'
title: Platform::FailureException, classe
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: 0b3f03888a92cc0c52e347ce5ee663a3e57b0b20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161258"
---
# <a name="platformfailureexception-class"></a>Platform::FailureException, classe

Levée lorsque l'opération a échoué. Il s'agit de l'équivalent de E_FAIL HRESULT.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Notes

Pour plus d'informations, consultez la classe [COMException](../cppcx/platform-comexception-class.md) .

### <a name="requirements"></a>Spécifications

**Client minimal pris en charge :** Windows 8

**Serveur minimal pris en charge :** Windows Server 2012

**Espace de noms :** Platform

**Métadonnées :** Platform. winmd

## <a name="see-also"></a>Voir aussi

[Platform :: COMException, classe](../cppcx/platform-comexception-class.md)

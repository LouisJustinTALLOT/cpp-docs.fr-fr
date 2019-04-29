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
ms.openlocfilehash: f527271b50382a9aec1585e139a0083135315473
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383332"
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

**Prise en charge minimale du client :** Windows 8

**Serveur pris en charge minimale :** Windows Server 2012

**Espace de noms :** Plateforme

**Métadonnées :** platform.winmd

## <a name="see-also"></a>Voir aussi

[Platform::COMException, classe](../cppcx/platform-comexception-class.md)

---
title: Exceptions (C/C++)
ms.date: 11/04/2016
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: 14440e625ffdb28b4b8daf6a78563ba839834213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647757"
---
# <a name="exceptions-cc"></a>Exceptions (C/C++)

Deux codes d’exception peuvent être déclenchés lorsque des défaillances sont rencontrées :

- Pour un **LoadLibrary** Échec

- Pour un **GetProcAddress** Échec

Voici les informations sur l’exception :

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Les codes d’exception levées sont les VcppException standard (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) et les valeurs de VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). L’exception passe un pointeur vers un **DelayLoadInfo** structure dans la valeur qui peut être récupérée par **GetExceptionInformation** dans le [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record) structure, champ ExceptionInformation [0].

En outre, si les bits incorrects sont définis dans le champ grAttrs, l’exception ERROR_INVALID_PARAMETER est levée. Cette exception est, par tous les cas, irrécupérable.

Consultez [définitions des structures et constantes](../../build/reference/structure-and-constant-definitions.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](../../build/reference/error-handling-and-notification.md)
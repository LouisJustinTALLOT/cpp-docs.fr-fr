---
title: Codes d’exception de chargement de DLLC++(C/)
ms.date: 11/19/2019
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
ms.openlocfilehash: f557fe736f45f8c3f5411d076a0be18f1d1b670e
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74243853"
---
# <a name="exceptions-cc"></a>Exceptions (C/C++)

Deux codes d’exception peuvent être déclenchés lorsque des erreurs sont rencontrées :

- Pour une erreur **LoadLibrary**

- Pour un échec **GetProcAddress**

Les informations sur les exceptions sont les suivantes :

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Les codes d’exception générés sont les valeurs standard VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) et VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). L’exception passe un pointeur vers une structure **DelayLoadInfo** dans la valeur LPDWORD qui peut être récupérée par **GetExceptionInformation** dans le champ de la structure [EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record) , ExceptionInformation [0].

En outre, si les bits incorrects sont définis dans le champ grAttrs, l’exception ERROR_INVALID_PARAMETER est levée. Cette exception est, pour toutes les intentions et les objectifs, fatale.

Pour plus d’informations, consultez [définitions de structure et de constantes](structure-and-constant-definitions.md) .

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](error-handling-and-notification.md)

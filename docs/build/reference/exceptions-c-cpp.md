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
ms.openlocfilehash: cf38af464f08e143ed9073befe30f6aeb8b913b6
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915458"
---
# <a name="exceptions-cc"></a>Exceptions (C/C++)

Deux codes d’exception peuvent être déclenchés lorsque des erreurs sont rencontrées:

- Pour une erreur **LoadLibrary**

- Pour un échec **GetProcAddress**

Les informations sur les exceptions sont les suivantes:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

Les codes d’exception générés sont les valeurs standard VcppException (ERROR_SEVERITY_ERROR, ERROR_MOD_NOT_FOUND) et VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND). L’exception passe un pointeur vers une structure **DelayLoadInfo** dans la valeur LPDWORD qui peut être récupérée par **GetExceptionInformation** dans le champ ExceptionInformation [0] de la structure [EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) .

En outre, si les bits incorrects sont définis dans le champ grAttrs, l’exception ERROR_INVALID_PARAMETER est levée. Cette exception est, pour toutes les intentions et les objectifs, fatale.

Pour plus d’informations, consultez [définitions de structure et](structure-and-constant-definitions.md) de constantes.

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](error-handling-and-notification.md)

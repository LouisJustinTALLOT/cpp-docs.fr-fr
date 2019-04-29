---
title: _set_abort_behavior
ms.date: 1/02/2018
apiname:
- _set_abort_behavior
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: 8b36a771a3694c6d01573d619990743c7ddc0f3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356684"
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Spécifie l’action à entreprendre quand un programme s’arrête anormalement.

> [!NOTE]
> N’utilisez pas le [abandonner](abort.md) (fonction) pour arrêter une application Microsoft Store, à l’exception de test ou de scénarios de débogage. Méthodes de programmation ou l’interface utilisateur pour fermer une application de Store ne sont pas autorisées en fonction de la [les stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
Nouvelle valeur de la [abandonner](abort.md) indicateurs.

*mask*<br/>
Masque pour le [abandonner](abort.md) indicateurs de bits à définir.

## <a name="return-value"></a>Valeur de retour

Ancienne valeur des indicateurs.

## <a name="remarks"></a>Notes

Il existe deux [abandonner](abort.md) indicateurs : **_WRITE_ABORT_MSG** et **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** détermine si un message texte utile est imprimé quand un programme s’arrête anormalement. Le message indique que l’application a appelé la [abandonner](abort.md) (fonction). Le comportement par défaut consiste à imprimer le message. **_CALL_REPORTFAULT**, si définie, spécifie qu’un vidage sur incident de Watson est généré et signalé quand [abandonner](abort.md) est appelée. Par défaut, le signalement de vidage sur incident est activé dans les builds non DEBUG.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>Voir aussi

[abort](abort.md)<br/>

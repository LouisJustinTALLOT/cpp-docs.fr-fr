---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: 06f72597a384cc5c90b2e345e62e13dee96c4dca
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913131"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Spécifie l’action à entreprendre quand un programme s’arrête anormalement.

> [!NOTE]
> N’utilisez pas la fonction [Abort](abort.md) pour arrêter une application Microsoft Store, sauf dans les scénarios de test ou de débogage. Les méthodes de programmation ou d’interface utilisateur pour fermer une application du Windows Store ne sont pas autorisées selon les [stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez la page relative au [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Paramètres

*flags*<br/>
Nouvelle valeur des indicateurs d' [abandon](abort.md) .

*masque*<br/>
Masque pour les bits d’indicateurs d' [abandon](abort.md) à définir.

## <a name="return-value"></a>Valeur de retour

Ancienne valeur des indicateurs.

## <a name="remarks"></a>Notes 

Il existe deux indicateurs d' [abandon](abort.md) : **_WRITE_ABORT_MSG** et **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** détermine si un message texte utile est imprimé lorsqu’un programme se termine anormalement. Le message indique que l’application a appelé la fonction d' [abandon](abort.md) . Le comportement par défaut consiste à imprimer le message. **_CALL_REPORTFAULT**, s’il est défini, spécifie qu’un vidage sur incident Watson est généré et signalé lorsque [Abort](abort.md) est appelé. Par défaut, le signalement de vidage sur incident est activé dans les builds non DEBUG.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

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

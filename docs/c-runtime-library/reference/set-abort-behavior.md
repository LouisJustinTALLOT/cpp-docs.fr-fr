---
title: _set_abort_behavior
ms.date: 01/02/2018
api_name:
- _set_abort_behavior
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
ms.openlocfilehash: a63d4e77a91dafa4500d5fef8e9b5e94ee28cfbd
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948666"
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

*mask*<br/>
Masque pour les bits d’indicateurs d' [abandon](abort.md) à définir.

## <a name="return-value"></a>Valeur de retour

Ancienne valeur des indicateurs.

## <a name="remarks"></a>Notes

Il existe deux indicateurs d' [abandon](abort.md) : **_WRITE_ABORT_MSG** et **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** détermine si un message texte utile est imprimé lorsqu’un programme se termine anormalement. Le message indique que l’application a appelé la fonction d' [abandon](abort.md) . Le comportement par défaut consiste à imprimer le message. **_CALL_REPORTFAULT**, s’il est défini, spécifie qu’un vidage sur incident Watson est généré et signalé lorsque [Abort](abort.md) est appelé. Par défaut, le signalement de vidage sur incident est activé dans les builds non DEBUG.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

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

---
title: raise
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: b38a3430274b2324e345be30ce9e38f0c2749fa3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338261"
---
# <a name="raise"></a>raise

Envoie un signal au programme en cours d’exécution.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application Microsoft Store, sauf dans les scénarios de test ou de débogage. Les moyens programmatiques ou d’interface utilisateur de fermer une application Store ne sont pas autorisés selon les politiques du [Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, voir [le cycle de vie de l’application UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Paramètres

*sig*<br/>
Signal à déclencher.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **raise** retourne 0. Sinon, elle retourne une valeur différente de zéro.

## <a name="remarks"></a>Notes

La fonction **raise** envoie *sig* au programme en cours d’exécution. Si un appel précédent à **signal** a installé une fonction de gestion de signal pour *sig*, **raise** exécute cette fonction. Si aucune fonction de gestionnaire n’a été installée, l’action par défaut associée à la valeur de signal *sig* est effectuée, comme suit.

|Signal|Signification|Default|
|------------|-------------|-------------|
|**SIGABRT**|Arrêt anormal|Termine le programme appelant avec le code de sortie 3|
|**SIGFPE**|Erreur de virgule flottante|Termine le programme appelant|
|**SIGILL**|Instruction non conforme|Termine le programme appelant|
|**SIGINT**|Interruption CTRL+C|Termine le programme appelant|
|**SIGSEGV**|Accès au stockage non conforme|Termine le programme appelant|
|**SIGTERM**|Demande d’arrêt envoyée au programme|Ignore le signal|

Si l’argument n’est pas un signal valide tel que spécifié ci-dessus, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si elle n’est pas manipulée, la fonction définit **errno** à **EINVAL** et renvoie une valeur non zéro.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**raise**|\<signal.h >|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[Signal](signal.md)<br/>

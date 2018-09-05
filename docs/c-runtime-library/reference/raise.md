---
title: raise | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- raise
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
- Raise
dev_langs:
- C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1bc3f52b97159a9caba6f80b4798d9588ec341d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685906"
---
# <a name="raise"></a>raise

Envoie un signal au programme en cours d’exécution.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application Microsoft Store, à l’exception de test ou de scénarios de débogage. Méthodes de programmation ou l’interface utilisateur pour fermer une application de Store ne sont pas autorisées en fonction de la [les stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

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

En cas de réussite, **raise** retourne 0. Dans le cas contraire, une valeur différente de zéro est retournée.

## <a name="remarks"></a>Notes

La fonction **raise** envoie *sig* au programme en cours d’exécution. Si un appel précédent à **signal** a installé une fonction de gestion de signal pour *sig*, **raise** exécute cette fonction. Si aucune fonction de gestionnaire n’a été installée, l’action par défaut associée à la valeur de signal *sig* est effectuée, comme suit.

|Signal|Signification|Par défaut|
|------------|-------------|-------------|
|**SIGABRT**|Arrêt anormal|Termine le programme appelant avec le code de sortie 3|
|**SIGFPE**|Erreur de virgule flottante|Termine le programme appelant|
|**SIGILL**|Instruction non conforme|Termine le programme appelant|
|**SIGINT**|Interruption CTRL+C|Termine le programme appelant|
|**SIGSEGV**|Accès au stockage non conforme|Termine le programme appelant|
|**SIGTERM**|Demande d’arrêt envoyée au programme|Ignore le signal|

Si l’argument n’est pas un signal valide tel que spécifié ci-dessus, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si non gérée, la fonction définit **errno** à **EINVAL** et retourne une valeur différente de zéro.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**raise**|\<signal.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>

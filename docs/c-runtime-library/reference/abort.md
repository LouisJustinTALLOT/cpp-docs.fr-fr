---
title: abort
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: 1f70f54783ce6f6d28fdda028af4fd5a205aeb0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350925"
---
# <a name="abort"></a>abort

Interrompt le processus actuel et retourne un code d’erreur.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application Microsoft Store ou une application Universal Windows Platform (UWP), sauf dans les scénarios de test ou de débogage. Les moyens programmatiques ou d’interface utilisateur de fermer une application Store ne sont pas autorisés selon les politiques du [Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, voir [le cycle de vie de l’application UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void abort( void );
```

## <a name="return-value"></a>Valeur de retour

**l’interruption** ne retourne pas le contrôle au processus d’appel. Par défaut, elle recherche un gestionnaire de signal d’abandon et déclenche `SIGABRT` si tel gestionnaire est défini. Puis **avorter** met fin au processus actuel et renvoie un code de sortie au processus parent.

## <a name="remarks"></a>Notes

**Microsoft Spécifique**

Par défaut, lorsqu’une application est construite avec la bibliothèque de temps `SIGABRT` d’exécution de déboguer, la routine **d’interruption** affiche un message d’erreur avant est soulevée. Pour les applications de console en cours d’exécution en mode console, le message est envoyé à `STDERR`. Les applications de bureau Windows et les applications de console qui s’exécutent en mode fenêtré affichent le message dans une boîte de message. Pour supprimer le message, utilisez [_set_abort_behavior](set-abort-behavior.md) pour effacer l’indicateur `_WRITE_ABORT_MSG`. Le message affiché dépend de la version de l’environnement d’exécution utilisé. Pour les applications construites en utilisant les versions les plus récentes de Visual CMD, le message ressemble à ceci :

> R6010 - avortement () a été appelé

Dans les versions précédentes de la bibliothèque runtime C, le message suivant était affiché :

> This application has requested the Runtime to terminate it in an unusual way. Please contact the application’s support team for more information.

Quand le programme est compilé en mode débogage, la boîte de message affiche les options **Abandonner**, **Réessayer** ou **Ignorer**. Si l’utilisateur choisit **Abandonner**, le programme se termine immédiatement et retourne le code de sortie 3. Si l’utilisateur choisit **Réessayer**, un débogueur est appelé pour le débogage juste-à-temps, si disponible. Si l’utilisateur choisit **Ignorer**, **avorter** continue le traitement normal.

Dans les constructions de détail et de débogé, **avorter** puis vérifie si un gestionnaire de signal d’interruption est réglé. Si un gestionnaire de signal non `raise(SIGABRT)`par défaut est réglé, **avortez les** appels . Utilisez la fonction [signal](signal.md) pour associer une fonction de gestionnaire de signal d’abandon au signal `SIGABRT`. Vous pouvez effectuer des actions personnalisées, telles que nettoyer les ressources ou enregistrer des informations, et arrêter l’application avec votre propre code d’erreur dans la fonction de gestionnaire. Si aucun gestionnaire de signal personnalisé n’est défini, **l’interruption** n’augmente pas le `SIGABRT` signal.

Par défaut, dans les versions non-débbug d’applications de bureau ou de console, **avorter** puis invoque le mécanisme de service de déclaration d’erreurs Windows (anciennement connu sous le nom de Dr Watson) pour signaler les défaillances de Microsoft. Vous pouvez activer ou désactiver ce comportement en appelant `_set_abort_behavior` et en définissant ou masquant l’indicateur `_CALL_REPORTFAULT`. Quand l’indicateur est défini, Windows affiche une boîte de message dont le texte ressemble à ceci : « Le programme a cessé de fonctionner correctement à cause d’un problème. » L’utilisateur peut choisir d’appeler un débogueur avec un bouton **Déboguer**, ou choisir le bouton **Fermer le programme** pour mettre fin à l’application avec un code d’erreur défini par le système d’exploitation.

Si le gestionnaire de déclaration d’erreur Windows n’est pas invoqué, puis **interrompre** les appels [_exit](exit-exit-exit.md) de mettre fin au processus avec le code de sortie 3 et retourne le contrôle au processus parent ou au système d’exploitation. `_exit` ne vide pas les mémoires tampons de flux ou n’effectue pas de traitement `atexit`/`_onexit`.

Pour plus d’informations sur le débogage CRT, consultez [Techniques de débogage CRT](/visualstudio/debugger/crt-debugging-techniques).

**FIN de la section spécifique à Microsoft**

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**abort**|\<process.h> ou \<stdlib.h>|

## <a name="example"></a>Exemple

Le programme suivant essaie d’ouvrir un fichier et s’interrompt si la tentative échoue.

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>Voir aussi

[Utilisation de abort](../../cpp/using-abort.md)<br/>
[abort Fonction](../../c-language/abort-function-c.md)<br/>
[Contrôle des processus et de l’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, fonctions _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[Signal](signal.md)<br/>
[_spawn, fonctions _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)

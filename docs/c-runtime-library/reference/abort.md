---
title: abort | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- abort
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
- Abort
dev_langs:
- C++
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 943faab6b13f3d07b2ca19d78c555973149aa4b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392612"
---
# <a name="abort"></a>abort

Interrompt le processus actuel et retourne un code d’erreur.

> [!NOTE]
> N’utilisez pas cette méthode pour arrêter une application Microsoft Store ou d’une application de plateforme Windows universelle (UWP), à l’exception de test ou de scénarios de débogage. Méthodes de programmation ou l’interface utilisateur pour fermer une application de magasin ne sont pas autorisées en fonction de la [des stratégies Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```c
void abort( void );
```

## <a name="return-value"></a>Valeur de retour

**abandonner** ne retourne pas de contrôle pour le processus appelant. Par défaut, il recherche un gestionnaire de signal d’abandon et déclenche **SIGABRT** si elle est définie. Puis **abandonner** termine le processus actuel et retourne un code de sortie pour le processus parent.

## <a name="remarks"></a>Notes

**Section spécifique à Microsoft**

Par défaut, lorsqu’une application est générée avec la bibliothèque runtime de débogage, le **abandonner** routine affiche un message d’erreur avant **SIGABRT** est déclenché. Pour les applications de console en cours d’exécution en mode console, le message est envoyé à **STDERR**. Les applications de bureau Windows et les applications de console qui s’exécutent en mode fenêtré affichent le message dans une boîte de message. Pour supprimer le message, utilisez [_set_abort_behavior](set-abort-behavior.md) pour effacer le **_WRITE_ABORT_MSG** indicateur. Le message affiché dépend de la version de l’environnement d’exécution utilisé. Pour les applications générées à l’aide des versions les plus récentes de Visual C++, le message ressemble à ceci :

> R6010 - abort() a été appelée.

Dans les versions précédentes de la bibliothèque runtime C, le message suivant était affiché :

> This application has requested the Runtime to terminate it in an unusual way. Please contact the application’s support team for more information.

Quand le programme est compilé en mode débogage, la boîte de message affiche les options **Abandonner**, **Réessayer** ou **Ignorer**. Si l’utilisateur choisit **Abandonner**, le programme se termine immédiatement et retourne le code de sortie 3. Si l’utilisateur choisit **Réessayer**, un débogueur est appelé pour le débogage juste-à-temps, si disponible. Si l’utilisateur choisit **ignorer**, **abandonner** continue le traitement normal.

Dans les versions commerciales et de débogage, **abandonner** vérifie ensuite si un gestionnaire de signal d’abandon est défini. Si un gestionnaire de signal de celle par défaut est défini, **abandonner** appelle `raise(SIGABRT)`. Utilisez le [signal](signal.md) fonction pour associer une fonction de gestionnaire de signal abandon avec la **SIGABRT** signal. Vous pouvez effectuer des actions personnalisées, telles que nettoyer les ressources ou enregistrer des informations, et arrêter l’application avec votre propre code d’erreur dans la fonction de gestionnaire. Si aucun gestionnaire de signal personnalisé est défini, **abandonner** ne déclenche pas la **SIGABRT** signal.

Par défaut, dans les versions non debug des applications de bureau ou de la console, **abandonner** appelle ensuite le mécanisme de Service de création de rapports d’erreurs Windows (autrefois appelé récupération d’urgence. Watson) pour signaler les échecs à Microsoft. Ce comportement peut être activé ou désactivé en appelant **_set_abort_behavior** et la définition ou de masquage du **_CALL_REPORTFAULT** indicateur. Quand l’indicateur est défini, Windows affiche une boîte de message dont le texte ressemble à ceci : « Le programme a cessé de fonctionner correctement à cause d’un problème. » L’utilisateur peut choisir d’appeler un débogueur avec un bouton **Déboguer**, ou choisir le bouton **Fermer le programme** pour mettre fin à l’application avec un code d’erreur défini par le système d’exploitation.

Si le Gestionnaire de rapport d’erreurs Windows n’est pas appelé, puis **abandonner** appelle [_exit](exit-exit-exit.md) mettre fin au processus avec sortie code 3 et retourne le contrôle au processus parent ou le système d’exploitation. **_exit** ne pas vider les mémoires tampons de flux de données ou faire **atexit**/**_onexit** de traitement.

Pour plus d'informations sur le débogage CRT, consultez [Techniques de débogage CRT](/visualstudio/debugger/crt-debugging-techniques).

**Fin de la section spécifique à Microsoft**

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

[Utilisation d’abort](../../cpp/using-abort.md)<br/>
[abort, fonction](../../c-language/abort-function-c.md)<br/>
[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)<br/>

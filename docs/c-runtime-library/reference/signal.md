---
title: signal
ms.date: 04/12/2018
apiname:
- signal
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
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 351bdbe1d787fc5e5d741460adfe415df7fda756
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356288"
---
# <a name="signal"></a>signal

Définit la gestion du signal d'interruption.

> [!IMPORTANT]
> N’utilisez pas cette méthode pour arrêter une application Microsoft Store, à l’exception de test ou de scénarios de débogage. Méthodes de programmation ou l’interface utilisateur pour fermer une application de Store ne sont pas autorisées en fonction de la [les stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Paramètres

*sig*<br/>
Valeur du signal.

*func*<br/>
Le deuxième paramètre est un pointeur vers la fonction à exécuter. Le premier paramètre est une valeur de signal et le deuxième paramètre est un sous-code qui peut être utilisé lorsque le premier paramètre est SIGFPE.

## <a name="return-value"></a>Valeur de retour

**signal** retourne la valeur précédente de func qui est associé au signal donné. Par exemple, si la valeur précédente de *func* a été **SIG_IGN**, la valeur de retour est également **SIG_IGN**. La valeur de retour **SIG_ERR** indique une erreur ; dans ce cas, **errno** a la valeur **EINVAL**.

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **signal** (fonction) permet à un processus choisir une des différentes méthodes pour gérer un signal d’interruption à partir du système d’exploitation. Le *sig* argument est l’interruption à laquelle **signal** répond ; il doit être une des constantes manifestes suivantes, qui sont définies dans le SIGNAL. H.

|*SIG* valeur|Description|
|-----------------|-----------------|
|**SIGABRT**|Arrêt anormal|
|**SIGFPE**|Erreur de virgule flottante|
|**SIGILL**|Instruction non conforme|
|**SIGINT**|Signal CTRL+C|
|**SIGSEGV**|Accès au stockage non conforme|
|**SIGTERM**|Demande d'arrêt|

Si *sig* ne fait pas partie des valeurs ci-dessus, le Gestionnaire de paramètre non valide est appelé, comme défini dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **SIG_ERR**.

Par défaut, **signal** termine le programme appelant avec le code de sortie 3, quelle que soit la valeur de *sig*.

> [!NOTE]
> **SIGINT** n’est pas pris en charge pour toutes les applications Win32. Lorsqu'une interruption CTRL+C se produit, les systèmes d'exploitation Win32 génèrent un nouveau thread pour gérer spécifiquement cette interruption. Cela peut amener une application à un seul thread, par exemple celle dans UNIX, à devenir multithread et à provoquer un comportement inattendu.

Le *func* argument est une adresse à un gestionnaire de signal que vous écrivez, ou à une des constantes prédéfinies **SIG_DFL** ou **SIG_IGN**, qui sont également définis dans le SIGNAL. H. Si *func* est une fonction, il est installé en tant que gestionnaire de signal pour le signal donné. Prototype du Gestionnaire de signal requiert un argument formel, *sig*, de type **int**. Le système d’exploitation fournit l’argument réel via *sig* lorsqu’une interruption se produit ; l’argument est le signal qui a généré l’interruption. Par conséquent, vous pouvez utiliser les six constantes de manifeste (répertoriées dans le tableau précédent) de votre gestionnaire de signal pour déterminer le type d'interruption et prendre les mesures appropriées. Par exemple, vous pouvez appeler **signal** à deux reprises pour assigner le même gestionnaire à deux signaux différents, puis tester la *sig* argument dans le gestionnaire pour prendre des mesures différentes selon le signal reçu.

Si vous testez pour les exceptions de virgule flottante (**SIGFPE**), *func* pointe vers une fonction qui accepte un deuxième argument facultatif qui est une de plusieurs constantes manifestes, définies dans FLOAT. H, sous la forme **FPE_xxx**. Quand un **SIGFPE** signal se produit, vous pouvez tester la valeur du deuxième argument pour déterminer le type d’exception à virgule flottante et agir en conséquence. Cet argument et ses valeurs possibles sont des extensions Microsoft.

Pour les exceptions à virgule flottante, la valeur de *func* n’est pas réinitialisée lorsque le signal est reçu. Pour récupérer des exceptions à virgule flottante, utilisez les clauses try/except pour cerner les opérations à virgule flottante. Il est aussi possible d’effectuer une récupération en utilisant [setjmp](setjmp.md) avec [longjmp](longjmp.md). Dans les deux cas, le processus appelant reprend l'exécution et quitte l'état à virgule flottante du processus non défini.

Si le gestionnaire de signal retourne, le processus appelant reprend l'exécution immédiatement après le moment où il a reçu le signal d'interruption. Cela est vrai quel que soit le type de signal ou le mode de fonctionnement.

Avant l’exécution de la fonction spécifiée, la valeur de *func* a la valeur **SIG_DFL**. Le signal d’interruption suivant est traité comme décrit pour **SIG_DFL**, sauf si un appel d’intervention à **signal** spécifie autrement. Vous pouvez utiliser cette fonctionnalité pour réinitialiser les signaux dans la fonction appelée.

Dans la mesure où les routines de gestion de signal sont généralement appelées de façon asynchrone lorsqu'une interruption se produit, votre fonction de gestion de signal peut obtenir le contrôle lorsqu'une opération du runtime est incomplète et dans un état inconnu. La liste suivante résume les restrictions qui déterminent les fonctions que vous pouvez utiliser dans votre routine de gestion de signal.

- Effectuez pas les problème de bas niveau STDIO. Les routines d’e/s H (par exemple, **printf** ou **fread**).

- N’appelez pas les routines du tas ou toute routine qui utilise les routines du tas (par exemple, **malloc**, **_strdup**, ou **_putenv**). Pour plus d’informations, consultez [malloc](malloc.md).

- N’utilisez pas de n’importe quelle fonction qui génère un appel système (par exemple, **_getcwd** ou **temps**).

- N’utilisez pas **longjmp** , sauf si l’interruption est provoquée par une exception de virgule flottante (autrement dit, *sig* est **SIGFPE**). Dans ce cas, réinitialisez d’abord le package à virgule flottante à l’aide d’un appel à **_fpreset**.

- N'utilisez aucune routine de superposition.

Un programme doit contenir un code à virgule flottante s’il doit intercepter le **SIGFPE** exception à l’aide de la fonction. Si votre programme ne contient pas de code à virgule flottante et qu'il requiert le code de gestion de signal de la bibliothèque runtime, déclarez un chiffre de type double volatile et initialisez-le à zéro :

```C
volatile double d = 0.0f;
```

Le **SIGILL** et **SIGTERM** signaux ne sont pas générés sous Windows. Ils sont inclus pour la compatibilité ANSI. Par conséquent, vous pouvez définir des gestionnaires de signal pour ces signaux à l’aide de **signal**, et vous pouvez générer également explicitement ces signaux en appelant [déclencher](raise.md).

Paramètres de signal ne sont pas conservés dans les processus engendrés qui sont créés par les appels à [_exec](../../c-runtime-library/exec-wexec-functions.md) ou [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) fonctions. Les valeurs par défaut des paramètres de signal sont réinitialisées dans le nouveau processus.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**signal**|\<signal.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser **signal** pour ajouter un comportement personnalisé pour le **SIGABRT** signal. Pour plus d’informations sur le comportement d’arrêt, consultez [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>
#include <tchar.h>

void SignalHandler(int signal)
{
    if (signal == SIGABRT) {
        // abort signal handler code
    } else {
        // ...
    }
}

int main()
{
    typedef void (*SignalHandlerPointer)(int);

    SignalHandlerPointer previousHandler;
    previousHandler = signal(SIGABRT, SignalHandler);

    abort();
}
```

```Output
This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec, fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn, fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>

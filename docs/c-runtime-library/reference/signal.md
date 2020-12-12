---
description: 'En savoir plus sur : signal'
title: signal
ms.date: 04/12/2018
api_name:
- signal
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
- signal
helpviewer_keywords:
- signal function
ms.openlocfilehash: 601e8108f7078356cdd1c6642deb05762b970e00
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97303451"
---
# <a name="signal"></a>signal

Définit la gestion du signal d'interruption.

> [!IMPORTANT]
> N’utilisez pas cette méthode pour arrêter une application Microsoft Store, sauf dans les scénarios de test ou de débogage. Les méthodes de programmation ou d’interface utilisateur pour fermer une application du Windows Store ne sont pas autorisées selon les [stratégies de Microsoft Store](/legal/windows/agreements/store-policies). Pour plus d’informations, consultez la page relative au [cycle de vie des applications UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntaxe

```C
void __cdecl *signal(int sig, int (*func)(int, int));
```

### <a name="parameters"></a>Paramètres

*McAfee*<br/>
Valeur du signal.

*func*<br/>
Le deuxième paramètre est un pointeur vers la fonction à exécuter. Le premier paramètre est une valeur de signal et le deuxième paramètre est un sous-code qui peut être utilisé lorsque le premier paramètre est SIGFPE.

## <a name="return-value"></a>Valeur renvoyée

**signal** retourne la valeur précédente de Func associée au signal donné. Par exemple, si la valeur précédente de *Func* était **SIG_IGN**, la valeur de retour est également **SIG_IGN**. Une valeur de retour de **SIG_ERR** indique une erreur ; dans ce cas, **errno** a la valeur **EINVAL**.

Pour plus d’informations sur les codes de retour, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **signal** permet à un processus de choisir l’une des méthodes permettant de gérer un signal d’interruption à partir du système d’exploitation. L’argument *SIG* est l’interruption sur laquelle le **signal** répond ; il doit s’agir de l’une des constantes manifestes suivantes, qui sont définies dans SIGNAL. H.

|valeur *SIG*|Description|
|-----------------|-----------------|
|**SIGABRT**|Arrêt anormal|
|**SIGFPE**|Erreur de virgule flottante|
|**SIGILL**|Instruction non conforme|
|**SIGINT**|Signal CTRL+C|
|**SIGSEGV**|Accès au stockage non conforme|
|**SIGTERM**|Demande d'arrêt|

Si *SIG* ne fait pas partie des valeurs ci-dessus, le gestionnaire de paramètre non valide est appelé, comme défini dans [validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne **SIG_ERR**.

Par défaut, le **signal** met fin au programme appelant avec le code de sortie 3, quelle que soit la valeur de *SIG*.

> [!NOTE]
> **SIGINT** n’est pris en charge pour aucune application Win32. Lorsqu'une interruption CTRL+C se produit, les systèmes d'exploitation Win32 génèrent un nouveau thread pour gérer spécifiquement cette interruption. Cela peut amener une application à un seul thread, par exemple celle dans UNIX, à devenir multithread et à provoquer un comportement inattendu.

L’argument *Func* est une adresse à un gestionnaire de signal que vous écrivez, ou à l’une des constantes prédéfinies **SIG_DFL** ou **SIG_IGN**, qui sont également définies dans signal. H. Si *Func* est une fonction, elle est installée en tant que gestionnaire de signal pour le signal donné. Le prototype du gestionnaire de signal requiert un argument formel, *SIG*, de type **`int`** . Le système d’exploitation fournit l’argument réel via *SIG* lorsqu’une interruption se produit ; l’argument est le signal qui a généré l’interruption. Par conséquent, vous pouvez utiliser les six constantes de manifeste (répertoriées dans le tableau précédent) de votre gestionnaire de signal pour déterminer le type d'interruption et prendre les mesures appropriées. Par exemple, vous pouvez appeler **signal** deux fois pour assigner le même gestionnaire à deux signaux différents, puis tester l’argument *SIG* dans le gestionnaire pour prendre des mesures différentes selon le signal reçu.

Si vous testez des exceptions à virgule flottante (**SIGFPE**), *Func* pointe vers une fonction qui accepte un deuxième argument facultatif qui est l’une des nombreuses constantes de manifeste, définies en valeur float. H, sous la forme **FPE_xxx**. Quand un signal **SIGFPE** se produit, vous pouvez tester la valeur du deuxième argument pour déterminer le type d’exception à virgule flottante, puis prendre les mesures appropriées. Cet argument et ses valeurs possibles sont des extensions Microsoft.

Pour les exceptions à virgule flottante, la valeur de *Func* n’est pas réinitialisée lorsque le signal est reçu. Pour récupérer des exceptions à virgule flottante, utilisez les clauses try/except pour cerner les opérations à virgule flottante. Il est aussi possible d’effectuer une récupération en utilisant [setjmp](setjmp.md) avec [longjmp](longjmp.md). Dans les deux cas, le processus appelant reprend l'exécution et quitte l'état à virgule flottante du processus non défini.

Si le gestionnaire de signal retourne, le processus appelant reprend l'exécution immédiatement après le moment où il a reçu le signal d'interruption. Cela est vrai quel que soit le type de signal ou le mode de fonctionnement.

Avant que la fonction spécifiée soit exécutée, la valeur de *Func* est définie sur **SIG_DFL**. Le signal d’interruption suivant est traité comme décrit pour **SIG_DFL**, à moins qu’un appel intermédiaire au **signal** spécifie autrement. Vous pouvez utiliser cette fonctionnalité pour réinitialiser les signaux dans la fonction appelée.

Dans la mesure où les routines de gestion de signal sont généralement appelées de façon asynchrone lorsqu'une interruption se produit, votre fonction de gestion de signal peut obtenir le contrôle lorsqu'une opération du runtime est incomplète et dans un état inconnu. La liste suivante résume les restrictions qui déterminent les fonctions que vous pouvez utiliser dans votre routine de gestion de signal.

- N’émettez pas de niveau inférieur ou STDIO. Routines d’e/s (par exemple, **printf** ou **fread**).

- N’appelez pas les routines de tas ou toute routine qui utilise les routines de tas (par exemple, **malloc**, **_strdup** ou **_putenv**). Pour plus d’informations, consultez [malloc](malloc.md).

- N’utilisez aucune fonction qui génère un appel système (par exemple, **_getcwd** ou une **heure**).

- N’utilisez pas **longjmp** à moins que l’interruption soit provoquée par une exception à virgule flottante (c’est-à-dire que *SIG* est **SIGFPE**). Dans ce cas, réinitialisez d’abord le package à virgule flottante à l’aide d’un appel à **_fpreset**.

- N'utilisez aucune routine de superposition.

Un programme doit contenir du code à virgule flottante s’il doit intercepter l’exception **SIGFPE** à l’aide de la fonction. Si votre programme ne contient pas de code à virgule flottante et qu'il requiert le code de gestion de signal de la bibliothèque runtime, déclarez un chiffre de type double volatile et initialisez-le à zéro :

```C
volatile double d = 0.0f;
```

Les signaux **SIGILL** et **SIGTERM** ne sont pas générés sous Windows. Ils sont inclus pour la compatibilité ANSI. Par conséquent, vous pouvez définir des gestionnaires de signal pour ces signaux à l’aide de **signal**, et vous pouvez également générer explicitement ces signaux en appelant [Raise](raise.md).

Les paramètres de signal ne sont pas conservés dans les processus générés créés par des appels à des fonctions [_exec](../../c-runtime-library/exec-wexec-functions.md) ou [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) . Les valeurs par défaut des paramètres de signal sont réinitialisées dans le nouveau processus.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**signal**|\<signal.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser **signal** pour ajouter un comportement personnalisé au signal **SIGABRT** . Pour plus d’informations sur le comportement d’arrêt, consultez [_set_abort_behavior](set-abort-behavior.md).

```C
// crt_signal.c
// compile with: /EHsc /W4
// Use signal to attach a signal handler to the abort routine
#include <stdlib.h>
#include <signal.h>

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

La sortie dépend de la version du runtime utilisée, du fait que l’application soit une console ou une application Windows, et sur les paramètres du Registre Windows. Pour une application console, un message semblable à celui-ci peut être envoyé à stderr :

```Output
Debug Error!

Program: c:\Projects\crt_signal\Debug\crt_signal.exe

R6010

- abort() has been called
```

## <a name="see-also"></a>Voir aussi

[Contrôle de processus et d’environnement](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[_exec, _wexec fonctions](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_fpreset](fpreset.md)<br/>
[_spawn, _wspawn fonctions](../../c-runtime-library/spawn-wspawn-functions.md)<br/>

---
title: Multithreading à l'aide de C et de Win32
ms.date: 08/09/2019
helpviewer_keywords:
- Windows API [C++], multithreading
- multithreading [C++], C and Win32
- Visual C, multithreading
- Win32 applications [C++], multithreading
- threading [C++], C and Win32
- Win32 [C++], multithreading
- threading [C]
ms.assetid: 67cdc99e-1ad9-452b-a042-ed246b70040e
ms.openlocfilehash: 1764561e0b2b43b8a89d8a1eb2e85d84ce33c4fc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422121"
---
# <a name="multithreading-with-c-and-win32"></a>Multithreading à l'aide de C et de Win32

Le compilateur Microsoft CC++ /MSVC fournit la prise en charge de la création d’applications multithread. Envisagez d’utiliser plusieurs threads si votre application doit effectuer des opérations coûteuses qui provoqueraient le blocage de l’interface utilisateur.

Avec MSVC, il existe plusieurs façons de programmer avec plusieurs threads : vous pouvez C++utiliser/WinRT et la bibliothèque Windows Runtime, la bibliothèque MFC (Microsoft Foundation Class) C++,/CLI et le Runtime .net, ou la bibliothèque Runtime C et l’API Win32. Cet article concerne le multithreading en C. Pour obtenir un exemple de code, consultez [exemple de programme multithread en C](sample-multithread-c-program.md).

## <a name="multithread-programs"></a>Programmes multithreads

Un thread est fondamentalement un chemin d’exécution via un programme. Il s’agit également de la plus petite unité d’exécution planifiée par Win32. Un thread se compose d’une pile, de l’état des registres de l’UC et d’une entrée dans la liste d’exécution du planificateur système. Chaque thread partage toutes les ressources du processus.

Un processus se compose d’un ou de plusieurs threads et du code, des données et d’autres ressources d’un programme en mémoire. Les ressources de programme standard sont les fichiers ouverts, les sémaphores et la mémoire allouée dynamiquement. Un programme s’exécute lorsque le planificateur système donne le contrôle d’exécution de l’un de ses threads. Le planificateur détermine les threads qui doivent s’exécuter et le moment où ils doivent s’exécuter. Les threads de priorité inférieure devront peut-être attendre que les threads de priorité supérieure terminent leurs tâches. Sur les ordinateurs multiprocesseurs, le planificateur peut déplacer des threads individuels vers différents processeurs pour équilibrer la charge du processeur.

Chaque thread dans un processus fonctionne de manière indépendante. À moins que vous ne les rendez visibles l’un à l’autre, les threads s’exécutent individuellement et ne connaissent pas les autres threads d’un processus. Toutefois, les threads partageant des ressources communes doivent coordonner leur travail à l’aide de sémaphores ou d’une autre méthode de communication entre processus. Pour plus d’informations sur la synchronisation des threads, consultez [écriture d’un programme Win32 multithread](#writing-a-multithreaded-win32-program).

## <a name="library-support-for-multithreading"></a>Prise en charge des bibliothèques pour le multithreading

Toutes les versions du CRT prennent désormais en charge le multithreading, à l’exception des versions sans verrouillage de certaines fonctions. Pour plus d’informations, consultez [performances des bibliothèques multithread](../c-runtime-library/multithreaded-libraries-performance.md). Pour plus d’informations sur les versions du CRT disponibles pour établir une liaison avec votre code, consultez fonctionnalités de la [bibliothèque CRT](../c-runtime-library/crt-library-features.md).

## <a name="include-files-for-multithreading"></a>Fichiers include pour le multithreading

Les fichiers include CRT standard déclarent les fonctions de la bibliothèque Runtime C telles qu’elles sont implémentées dans les bibliothèques. Si vos options de compilateur spécifient les conventions d’appel [__fastcall ou __vectorcall](../build/reference/gd-gr-gv-gz-calling-convention.md) , le compilateur suppose que toutes les fonctions doivent être appelées à l’aide de la Convention d’appel du Registre. Les fonctions de la bibliothèque Runtime utilisent la Convention d’appel C, et les déclarations dans les fichiers Include standard indiquent au compilateur de générer des références externes correctes à ces fonctions.

## <a name="crt-functions-for-thread-control"></a>Fonctions CRT pour le contrôle de thread

Tous les programmes Win32 disposent d’au moins un thread. Tout thread peut créer des threads supplémentaires. Un thread peut terminer rapidement son travail, puis se terminer, ou rester actif pendant toute la durée de vie du programme.

Les bibliothèques CRT fournissent les fonctions suivantes pour la création et l’arrêt des threads : [_beginthread, _beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md), [_endthread et _endthreadex](../c-runtime-library/reference/endthread-endthreadex.md).

Les fonctions `_beginthread` et `_beginthreadex` créent un nouveau thread et retournent un identificateur de thread si l’opération réussit. Le thread se termine automatiquement s’il termine l’exécution. Sinon, elle peut se terminer avec un appel à `_endthread` ou `_endthreadex`.

> [!NOTE]
> Si vous appelez des routines runtime C à partir d’un programme créé à l’aide de LIBCMT. lib, vous devez démarrer vos threads avec la fonction `_beginthread` ou `_beginthreadex`. N’utilisez pas les fonctions Win32 `ExitThread` et `CreateThread`. L’utilisation de `SuspendThread` peut entraîner un blocage lorsque plusieurs threads sont bloqués en attendant que le thread suspendu achève son accès à une structure de données Runtime C.

### <a name="_core_the__beginthread_function"></a>Fonctions _beginthread et _beginthreadex

Les fonctions `_beginthread` et `_beginthreadex` créent un nouveau thread. Un thread partage le code et les segments de données d’un processus avec d’autres threads dans le processus, mais possède ses propres valeurs de Registre uniques, l’espace de pile et l’adresse d’instruction actuelle. Le système transmet le temps processeur à chaque thread, afin que tous les threads d’un processus puissent s’exécuter simultanément.

`_beginthread` et `_beginthreadex` sont similaires à la fonction [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) dans l’API Win32, mais elles présentent les différences suivantes :

- Ils initialisent certaines variables de la bibliothèque Runtime C. Cela est important uniquement si vous utilisez la bibliothèque Runtime C dans vos threads.

- `CreateThread` permettent de contrôler les attributs de sécurité. Vous pouvez utiliser cette fonction pour démarrer un thread dans un état suspendu.

`_beginthread` et `_beginthreadex` retourner un handle au nouveau thread en cas de réussite ou un code d’erreur en cas d’erreur.

### <a name="_core_the__endthread_function"></a>Fonctions _endthread et _endthreadex

La fonction [_endthread](../c-runtime-library/reference/endthread-endthreadex.md) termine un thread créé par `_beginthread` (et de la même façon, `_endthreadex` met fin à un thread créé par `_beginthreadex`). Les threads se terminent automatiquement lorsqu’ils se terminent. `_endthread` et `_endthreadex` sont utiles pour l’arrêt conditionnel à partir d’un thread. Par exemple, un thread dédié au traitement des communications peut se fermer s’il ne parvient pas à obtenir le contrôle du port de communication.

## <a name="writing-a-multithreaded-win32-program"></a>Écriture d’un programme Win32 multithread

Lorsque vous écrivez un programme avec plusieurs threads, vous devez coordonner leur comportement et leur [utilisation des ressources du programme](#_core_sharing_common_resources_between_threads). En outre, assurez-vous que chaque thread reçoit [sa propre pile](#_core_thread_stacks).

### <a name="_core_sharing_common_resources_between_threads"></a>Partage de ressources communes entre threads

> [!NOTE]
> Pour une discussion similaire du point de vue MFC, consultez [Multithreading : conseils de programmation](multithreading-programming-tips.md) et [Multithreading : quand utiliser les classes de synchronisation](multithreading-when-to-use-the-synchronization-classes.md).

Chaque thread possède sa propre pile et sa propre copie des registres de l’UC. D’autres ressources, telles que les fichiers, les données statiques et la mémoire du tas, sont partagées par tous les threads du processus. Les threads qui utilisent ces ressources communes doivent être synchronisés. Win32 offre plusieurs moyens de synchroniser les ressources, notamment les sémaphores, les sections critiques, les événements et les mutex.

Lorsque plusieurs threads accèdent à des données statiques, votre programme doit indiquer les éventuels conflits de ressources. Prenons l’exemple d’un programme où un thread met à jour une structure de données statiques contenant des coordonnées *x*,*y* pour les éléments qui doivent être affichés par un autre thread. Si le thread de mise à jour modifie la coordonnée *x* et s’il est devancé avant de pouvoir modifier la coordonnée *y* , le thread d’affichage peut être planifié avant la mise à jour de la coordonnée *y* . L’élément s’affiche à un emplacement incorrect. Vous pouvez éviter ce problème en utilisant des sémaphores pour contrôler l’accès à la structure.

Un mutex (Short pour *Mut*, *ex*clusion) est un moyen de communiquer entre les threads ou les processus qui s’exécutent de façon asynchrone l’un l’autre. Cette communication peut être utilisée pour coordonner les activités de plusieurs threads ou processus, généralement en contrôlant l’accès à une ressource partagée par le verrouillage et le déverrouillage de la ressource. Pour résoudre ce problème de mise à jour de coordonnées *x*,*y* , le thread de mise à jour définit un mutex indiquant que la structure de données est en cours d’utilisation avant d’effectuer la mise à jour. Il efface le mutex après le traitement des deux coordonnées. Le thread d’affichage doit attendre que le mutex soit clair avant de mettre à jour l’affichage. Ce processus d’attente d’un mutex est souvent appelé *blocage* sur un mutex, car le processus est bloqué et ne peut pas continuer tant que le mutex n’a pas été effacé.

Le programme Bounce. c présenté dans [exemple de programme multithread c](sample-multithread-c-program.md) utilise un mutex nommé `ScreenMutex` pour coordonner les mises à jour de l’écran. Chaque fois que l’un des threads d’affichage est prêt à écrire sur l’écran, il appelle `WaitForSingleObject` avec le handle pour `ScreenMutex` et une constante infinie pour indiquer que l’appel de `WaitForSingleObject` doit se bloquer sur le mutex et ne pas expirer. Si `ScreenMutex` est désactivée, la fonction Wait définit le mutex afin que d’autres threads ne puissent pas interférer avec l’affichage et continue à exécuter le thread. Sinon, le thread se bloque jusqu’à ce que le mutex soit effacé. Lorsque le thread termine la mise à jour d’affichage, il libère le mutex en appelant `ReleaseMutex`.

Les affichages d’écran et les données statiques ne sont que deux des ressources nécessitant une gestion soigneuse. Par exemple, votre programme peut avoir plusieurs threads qui accèdent au même fichier. Étant donné qu’un autre thread a peut-être déplacé le pointeur de fichier, chaque thread doit réinitialiser le pointeur de fichier avant la lecture ou l’écriture. En outre, chaque thread doit s’assurer qu’il n’est pas préempté entre le moment où il positionne le pointeur et le moment où il accède au fichier. Ces threads doivent utiliser un sémaphore pour coordonner l’accès au fichier en délimitant chaque accès aux fichiers avec des appels `WaitForSingleObject` et `ReleaseMutex`. L’exemple de code suivant illustre cette technique :

```C
HANDLE    hIOMutex = CreateMutex (NULL, FALSE, NULL);

WaitForSingleObject( hIOMutex, INFINITE );
fseek( fp, desired_position, 0L );
fwrite( data, sizeof( data ), 1, fp );
ReleaseMutex( hIOMutex);
```

### <a name="_core_thread_stacks"></a>Piles de threads

Tout l’espace de pile par défaut d’une application est alloué au premier thread d’exécution, appelé thread 1. Par conséquent, vous devez spécifier la quantité de mémoire à allouer pour une pile distincte pour chaque thread supplémentaire dont votre programme a besoin. Le système d’exploitation alloue de l’espace de pile supplémentaire pour le thread, si nécessaire, mais vous devez spécifier une valeur par défaut.

Le premier argument de l’appel de `_beginthread` est un pointeur vers la fonction `BounceProc`, qui exécute les threads. Le deuxième argument spécifie la taille de la pile par défaut pour le thread. Le dernier argument est un numéro d’ID qui est passé à `BounceProc`. `BounceProc` utilise le numéro d’identification pour amorcer le générateur de nombres aléatoires et sélectionner l’attribut de couleur et le caractère d’affichage du thread.

Les threads qui effectuent des appels à la bibliothèque Runtime C ou à l’API Win32 doivent autoriser un espace de pile suffisant pour la bibliothèque et les fonctions API qu’ils appellent. La fonction C `printf` nécessite plus de 500 octets d’espace de pile et vous devez disposer de 2 000 octets d’espace de pile lors de l’appel de routines d’API Win32.

Étant donné que chaque thread possède sa propre pile, vous pouvez éviter les collisions potentielles sur les éléments de données en utilisant aussi peu de données statiques que possible. Concevez votre programme pour qu’il utilise des variables de pile automatiques pour toutes les données qui peuvent être privées d’un thread. Les seules variables globales dans le programme Bounce. c sont soit des mutex, soit des variables qui ne changent jamais une fois qu’elles sont initialisées.

Win32 fournit également un stockage local des threads (TLS) pour stocker les données par thread. Pour plus d’informations, consultez [stockage local des threads (TLS)](thread-local-storage-tls.md).

## <a name="avoiding-problem-areas-with-multithread-programs"></a>Éviter les sources de problèmes dans les programmes multithreads

Il existe plusieurs problèmes que vous pouvez rencontrer lors de la création, de la liaison ou de l’exécution d’un programme multithread en langage C. Certains des problèmes les plus courants sont décrits dans le tableau suivant. (Pour une discussion similaire du point de vue MFC, consultez [Multithreading : conseils de programmation](multithreading-programming-tips.md).)

|Problème|Cause probable|
|-------------|--------------------|
|Vous recevez une boîte de message indiquant que votre programme a provoqué une violation de protection.|De nombreuses erreurs de programmation Win32 provoquent des violations de la protection. Une cause courante de violations de la protection est l’affectation indirecte de données aux pointeurs null. Étant donné que votre programme tente d’accéder à la mémoire qui n’y appartient pas, une violation de protection est émise.<br /><br /> Un moyen simple de détecter la cause d’une violation de protection consiste à compiler votre programme avec des informations de débogage, puis à l’exécuter par le biais du débogueur dans l’environnement Visual Studio. Lorsque l’erreur de protection se produit, Windows transfère le contrôle au débogueur et le curseur est positionné sur la ligne à l’origine du problème.|
|Votre programme génère de nombreuses erreurs de compilation et de liaison.|Vous pouvez éliminer de nombreux problèmes potentiels en définissant le niveau d’avertissement du compilateur sur l’une de ses valeurs les plus élevées et en respectant les messages d’avertissement. En utilisant les options de niveau d’avertissement de niveau 3 ou 4, vous pouvez détecter les conversions de données involontaires, les prototypes de fonction manquants et l’utilisation de fonctionnalités non-ANSI.|

## <a name="see-also"></a>Voir aussi

[Prise en charge du multithreading pour le C++code plus ancien (visuel)](multithreading-support-for-older-code-visual-cpp.md)\
[Exemple de programme multithread en C](sample-multithread-c-program.md)\
[Stockage local des threads (TLS)](thread-local-storage-tls.md)\
[Opérations d’accès concurrentiel et asynchrones avec C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency)\
[Multithreading à l’aide de C++ et de MFC](multithreading-with-cpp-and-mfc.md)

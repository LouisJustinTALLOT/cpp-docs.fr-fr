---
title: Lier un exécutable à une DLL
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: 2f907fedcaaf9897749ee0eb6a7ea5a33e1af679
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417361"
---
# <a name="link-an-executable-to-a-dll"></a>Lier un exécutable à une DLL

Un fichier exécutable lie (ou charge) une DLL de l’une des deux manières suivantes :

- *Liaison implicite*, où le système d’exploitation charge la dll en même temps que l’exécutable qui l’utilise. L’exécutable client appelle les fonctions exportées de la DLL de la même façon que si les fonctions étaient liées statiquement et contenues dans l’exécutable. La liaison implicite est parfois désignée sous le terme de *liaison dynamique*de charge ou de *charge statique* .

- *Liaison explicite*, où le système d’exploitation charge la dll à la demande au moment de l’exécution. Un exécutable qui utilise une DLL par liaison explicite doit charger et décharger explicitement la DLL. Il doit également configurer un pointeur de fonction pour accéder à chaque fonction qu’il utilise à partir de la DLL. Contrairement aux appels aux fonctions d’une bibliothèque liée de manière statique ou à une DLL implicitement liée, l’exécutable client doit appeler les fonctions exportées dans une DLL explicitement liée par le biais de pointeurs de fonction. La liaison explicite est parfois appelée liaison dynamique de *charge* ou de la *liaison dynamique au moment*de l’exécution.

Un exécutable peut utiliser la méthode de liaison pour établir une liaison à la même DLL. En outre, ces méthodes ne s’excluent pas mutuellement ; un exécutable peut être lié de manière implicite à une DLL et un autre peut s’y attacher explicitement.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Déterminer la méthode de liaison à utiliser

L’utilisation de la liaison implicite ou de la liaison explicite est une décision architecturale que vous devez prendre pour votre application. Chaque méthode présente des avantages et des inconvénients.

### <a name="implicit-linking"></a>Liaison implicite

La liaison implicite se produit lorsque le code d’une application appelle une fonction DLL exportée. Lorsque le code source de l’exécutable appelant est compilé ou assemblé, l’appel de fonction DLL génère une référence de fonction externe dans le code de l’objet. Pour résoudre cette référence externe, l’application doit établir une liaison avec la bibliothèque d’importation (fichier. lib) fournie par le créateur de la DLL.

La bibliothèque d’importation contient uniquement du code pour charger la DLL et pour implémenter des appels aux fonctions dans la DLL. La recherche d’une fonction externe dans une bibliothèque d’importation indique à l’éditeur de liens que le code de cette fonction se trouve dans une DLL. Pour résoudre des références externes à des dll, l’éditeur de liens ajoute simplement des informations au fichier exécutable qui indique au système où trouver le code DLL au démarrage du processus.

Lorsque le système démarre un programme qui contient des références liées de manière dynamique, il utilise les informations du fichier exécutable du programme pour localiser les dll requises. S’il ne peut pas localiser la DLL, le système met fin au processus et affiche une boîte de dialogue qui signale l’erreur. Dans le cas contraire, le système mappe les modules DLL dans l’espace d’adressage du processus.

Si l’une des dll a une fonction de point d’entrée pour l’initialisation et le code d’arrêt, comme `DllMain`, le système d’exploitation appelle la fonction. L’un des paramètres passés à la fonction de point d’entrée spécifie un code qui indique que la DLL est attachée au processus. Si la fonction de point d’entrée ne retourne pas la valeur TRUE, le système met fin au processus et signale l’erreur.

Enfin, le système modifie le code exécutable du processus pour fournir des adresses de démarrage pour les fonctions DLL.

À l’instar du reste du code d’un programme, le chargeur mappe le code de la DLL dans l’espace d’adressage du processus au démarrage du processus. Le système d’exploitation le charge en mémoire uniquement lorsque cela est nécessaire. Par conséquent, les attributs de code `PRELOAD` et `LOADONCALL` utilisés par les fichiers. def pour contrôler le chargement dans les versions précédentes de Windows n’ont plus de sens.

### <a name="explicit-linking"></a>Liaison explicite

La plupart des applications utilisent la liaison implicite, car il s’agit de la méthode de liaison la plus simple à utiliser. Toutefois, il existe des situations où une liaison explicite est nécessaire. Voici quelques raisons courantes d’utiliser la liaison explicite :

- L’application ne connaît pas le nom d’une DLL qu’elle charge jusqu’au moment de l’exécution. Par exemple, l’application peut obtenir le nom de la DLL et les fonctions exportées à partir d’un fichier de configuration au démarrage.

- Un processus qui utilise la liaison implicite est arrêté par le système d’exploitation si la DLL est introuvable au démarrage du processus. Un processus qui utilise la liaison explicite ne se termine pas dans cette situation et peut tenter de récupérer à partir de l’erreur. Par exemple, le processus peut informer l’utilisateur de l’erreur et demander à l’utilisateur de spécifier un autre chemin d’accès à la DLL.

- Un processus qui utilise la liaison implicite est également terminé si l’une des dll auxquelles il est lié a une fonction `DllMain` qui échoue. Un processus qui utilise la liaison explicite ne se termine pas dans cette situation.

- Une application qui lie implicitement à de nombreuses dll peut être lente à démarrer parce que Windows charge toutes les dll lors du chargement de l’application. Pour améliorer les performances de démarrage, une application peut uniquement utiliser la liaison implicite pour les dll requises immédiatement après le chargement. Elle peut utiliser la liaison explicite pour charger d’autres dll uniquement lorsqu’elles sont nécessaires.

- Les liaisons explicites éliminent le besoin de lier l’application à l’aide d’une bibliothèque d’importation. Si les modifications apportées à la DLL entraînent la modification des ordinaux d’exportation, les applications n’ont pas besoin de se relier s’ils appellent `GetProcAddress` à l’aide du nom d’une fonction et non d’une valeur ordinale. Les applications qui utilisent la liaison implicite doivent toujours être liées à la bibliothèque d’importation modifiée.

Voici deux dangers de la liaison explicite à connaître :

- Si la DLL a une fonction de point d’entrée `DllMain`, le système d’exploitation appelle la fonction dans le contexte du thread qui a appelé `LoadLibrary`. La fonction de point d’entrée n’est pas appelée si la DLL est déjà attachée au processus en raison d’un appel précédent à `LoadLibrary` qui n’avait aucun appel correspondant à la fonction `FreeLibrary`. La liaison explicite peut entraîner des problèmes si la DLL utilise une fonction `DllMain` pour initialiser chaque thread d’un processus, car tous les threads qui existent déjà quand `LoadLibrary` (ou `AfxLoadLibrary`) est appelé ne sont pas initialisés.

- Si une DLL déclare des données d’étendue statique comme `__declspec(thread)`, elle peut provoquer une erreur de protection si elle est liée de manière explicite. Une fois que la DLL est chargée par un appel à `LoadLibrary`, elle provoque une erreur de protection chaque fois que le code fait référence à ces données. (Les données d’étendue statiques incluent à la fois des éléments statiques globaux et locaux.) C’est pourquoi, lorsque vous créez une DLL, vous devez éviter d’utiliser le stockage local des threads. Si ce n’est pas le cas, Informez vos utilisateurs de DLL à propos des pièges potentiels de chargement dynamique de votre DLL. Pour plus d’informations, consultez [utilisation du stockage local des threads dans une bibliothèque de liens dynamiques (SDK Windows)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Comment utiliser la liaison implicite

Pour utiliser une DLL par liaison implicite, les exécutables clients doivent obtenir ces fichiers auprès du fournisseur de la DLL :

- Un ou plusieurs fichiers d’en-tête (fichiers. h) qui contiennent les déclarations des données, fonctions et C++ classes exportées dans la dll. Les classes, les fonctions et les données exportées par la DLL doivent toutes être marquées `__declspec(dllimport)` dans le fichier d’en-tête. Pour plus d’informations, consultez [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Bibliothèque d’importation à lier à votre fichier exécutable. L’éditeur de liens crée la bibliothèque d’importation lorsque la DLL est générée. Pour plus d’informations, consultez [fichiers lib en tant qu’entrée dans l’éditeur de liens](reference/dot-lib-files-as-linker-input.md).

- Fichier DLL réel.

Pour utiliser les données, les fonctions et les classes d’une DLL par liaison implicite, tout fichier source client doit inclure les fichiers d’en-tête qui les déclarent. Du point de vue du codage, les appels aux fonctions exportées sont similaires à tout autre appel de fonction.

Pour générer le fichier exécutable du client, vous devez créer un lien avec la bibliothèque d’importation de la DLL. Si vous utilisez un fichier Make externe ou un système de génération, spécifiez la bibliothèque d’importation avec les autres fichiers objets ou bibliothèques que vous liez.

Le système d’exploitation doit être en mesure de localiser le fichier DLL lorsqu’il charge l’exécutable appelant. Cela signifie que vous devez déployer ou vérifier l’existence de la DLL lorsque vous installez votre application.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Liaison explicite à une DLL

Pour utiliser une DLL par liaison explicite, les applications doivent effectuer un appel de fonction pour charger explicitement la DLL au moment de l’exécution. Pour établir une liaison explicite à une DLL, une application doit :

- Appelez [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) ou une fonction similaire pour charger la dll et obtenir un handle de module.

- Appelez [GetProcAddress](getprocaddress.md) pour obtenir un pointeur de fonction vers chaque fonction exportée appelée par l’application. Étant donné que les applications appellent les fonctions DLL via un pointeur, le compilateur ne génère pas de références externes, donc il n’est pas nécessaire d’établir une liaison avec une bibliothèque d’importation. Toutefois, vous devez disposer d’une instruction `typedef` ou `using` qui définit la signature d’appel des fonctions exportées que vous appelez.

- Appelez [FreeLibrary](freelibrary-and-afxfreelibrary.md) quand vous avez terminé avec la dll.

Par exemple, cet exemple de fonction appelle `LoadLibrary` pour charger une DLL nommée « MyDLL », appelle `GetProcAddress` pour obtenir un pointeur vers une fonction nommée « DLLFunc1 », appelle la fonction et enregistre le résultat, puis appelle `FreeLibrary` pour décharger la DLL.

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

Contrairement à cet exemple, dans la plupart des cas, vous devez appeler `LoadLibrary` et `FreeLibrary` une seule fois dans votre application pour une DLL donnée. Cela est particulièrement vrai si vous envisagez d’appeler plusieurs fonctions dans la DLL ou d’appeler des fonctions DLL à plusieurs reprises.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [Utilisation de bibliothèques d’importation et de fichiers d’exportation](reference/working-with-import-libraries-and-export-files.md)

- [Ordre de recherche de la bibliothèque de liens dynamiques](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)

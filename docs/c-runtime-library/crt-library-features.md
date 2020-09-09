---
title: Fonctions de bibliothèque CRT
description: Les fichiers qui contiennent les bibliothèques Runtime C de Microsoft, ainsi que les options de compilateur et les directives de préprocesseur associées.
ms.date: 09/03/2020
helpviewer_keywords:
- MSVCR71.dll
- libraries [C++], multithreaded
- library files, run-time
- LIBCMT.lib
- LIBCP.lib
- LIBCPMT.lib
- run-time libraries, C
- CRT, release versions
- MSVCP71.dll
- LIBC.lib
- libraries [C++]
- libraries [C++], run-time
- linking [C++], libraries
ms.assetid: a889fd39-807d-48f2-807f-81492612463f
ms.openlocfilehash: 2f46577ba81c57c2050f0cae4ae2af73152ba2a4
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609104"
---
# <a name="crt-library-features"></a>Fonctions de bibliothèque CRT

Cette rubrique décrit les différents fichiers .lib qui composent les bibliothèques Runtime C, ainsi que les options de compilateur et les directives de préprocesseur qui y sont associées.

## <a name="c-run-time-libraries-crt"></a>Bibliothèques runtime C (CRT)

La bibliothèque runtime C (CRT) est la partie de la bibliothèque C++ standard qui incorpore la bibliothèque ISO C99 standard. Les bibliothèques Visual C++ qui implémentent le CRT prennent en charge le développement du code natif ainsi que le code natif et managé mixte. Toutes les versions du CRT prennent en charge le développement multithread. La plupart des bibliothèques prennent en charge la liaison statique, pour lier la bibliothèque directement à votre code, ou la liaison dynamique pour permettre à votre code d’utiliser les fichiers DLL communs.

À compter de Visual Studio 2015, le CRT est refactorisé dans de nouveaux binaires. La bibliothèque Universal CRT (UCRT) contient les fonctions et variables globales exportées par la bibliothèque CRT C99 standard. UCRT est désormais un composant Windows fourni avec Windows 10. La bibliothèque statique, la bibliothèque d’importation de DLL et les fichiers d’en-tête UCRT se trouvent désormais dans le SDK Windows 10. Quand vous installez Visual C++, le programme d’installation de Visual Studio installe le sous-ensemble du SDK Windows 10 nécessaire à l’utilisation de l’UCRT. Vous pouvez utiliser l’UCRT sur n’importe quelle version de Windows prise en charge par Visual Studio 2015 et ultérieur. Vous pouvez la redistribuer à l’aide de vcredist pour les versions prises en charge de Windows distinctes de Windows 10. Pour plus d’informations, consultez [Redistribution des fichiers Visual C++](../windows/redistributing-visual-cpp-files.md).

Le tableau suivant répertorie les bibliothèques qui implémentent l’UCRT.

| Bibliothèque | DLL associée | Caractéristiques | Option | Directives de préprocesseur |
|--|--|--|--|--|
| *`libucrt.lib`* | None | Lie de manière statique l’UCRT à votre code. | **`/MT`** | `_MT` |
| *`libucrtd.lib`* | None | Version Debug de l’UCRT pour la liaison statique. Non redistribuable. | **`/MTd`** | `_DEBUG`, `_MT` |
| *`ucrt.lib`* | *`ucrtbase.dll`* | Bibliothèque d’importation de DLL pour l’UCRT. | **`/MD`** | `_MT`, `_DLL` |
| *`ucrtd.lib`* | *`ucrtbased.dll`* | Bibliothèque d’importation de DLL pour la version Debug de l’UCRT. Non redistribuable. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

La bibliothèque vcruntime contient le code spécifique à l’implémentation du CRT Visual C++, par exemple la gestion des exceptions et la prise en charge du débogage, les vérifications à l’exécution et les informations de type, les détails d’implémentation, ainsi que certaines fonctions de bibliothèque étendues. Cette bibliothèque est spécifique à la version du compilateur utilisé.

Ce tableau répertorie les bibliothèques qui implémentent la bibliothèque vcruntime.

| Bibliothèque | DLL associée | Caractéristiques | Option | Directives de préprocesseur |
|--|--|--|--|--|
| *`libvcruntime.lib`* | None | Liée de manière statique à votre code. | **`/MT`** | `_MT` |
| *`libvcruntimed.lib`* | None | Version Debug pour la liaison statique. Non redistribuable. | **`/MTd`** | `_MT`, `_DEBUG` |
| *`vcruntime.lib`* | *`vcruntime<version>.dll`* | Bibliothèque d’importation de DLL pour vcruntime. | **`/MD`** | `_MT`, `_DLL` |
| *`vcruntimed.lib`* | *`vcruntime<version>d.dll`* | Bibliothèque d’importation de DLL pour le vcruntime de débogage. Non redistribuable. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

> [!NOTE]
> Lorsque la refactorisation UCRT s’est produite, les fonctions runtime d’accès concurrentiel ont été déplacées *`concrt140.dll`* vers, qui a été ajouté au package redistribuable C++. Cette DLL est obligatoire pour les conteneurs et algorithmes parallèles C++ tels que `concurrency::parallel_for`. De plus, la bibliothèque standard C++ nécessite cette DLL sur Windows XP pour permettre la prise en charge des primitives de synchronisation, car Windows XP n’a pas de variables de condition.

Le code qui initialise le CRT se trouve dans l’une des nombreuses bibliothèques, selon que la bibliothèque CRT est liée de manière statique ou dynamique, ou que le code est natif, managé ou mixte. Ce code gère le démarrage du CRT, l’initialisation interne des données par thread, et l’arrêt. Il est spécifique à la version du compilateur utilisé. Cette bibliothèque est toujours liée de manière statique, même quand vous utilisez un UCRT lié de manière dynamique.

Ce tableau répertorie les bibliothèques qui implémentent l’initialisation et l’arrêt du CRT.

| Bibliothèque | Caractéristiques | Option | Directives de préprocesseur |
|--|--|--|--|
| *`libcmt.lib`* | Lie de manière statique le démarrage du CRT natif à votre code. | **`/MT`** | `_MT` |
| *`libcmtd.lib`* | Lie de manière statique la version Debug du démarrage du CRT natif. Non redistribuable. | **`/MTd`** | `_DEBUG`, `_MT` |
| *`msvcrt.lib`* | Bibliothèque statique pour le démarrage du CRT natif à utiliser avec les DLL UCRT et vcruntime. | **`/MD`** | `_MT`, `_DLL` |
| *`msvcrtd.lib`* | Bibliothèque statique pour la version Debug du démarrage du CRT natif à utiliser avec les DLL UCRT et vcruntime. Non redistribuable. | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |
| *`msvcmrt.lib`* | Bibliothèque statique pour le démarrage du CRT natif et managé mixte à utiliser avec les DLL UCRT et vcruntime. | **`/clr`** |  |
| *`msvcmrtd.lib`* | Bibliothèque statique pour la version Debug du démarrage du CRT natif et managé mixte à utiliser avec les DLL UCRT et vcruntime. Non redistribuable. | **`/clr`** |  |
| *`msvcurt.lib`* | **Déprécié** Bibliothèque statique pour le CRT managé pur. | **`/clr:pure`** |  |
| *`msvcurtd.lib`* | **Déprécié** Bibliothèque statique pour la version Debug du CRT managé pur. Non redistribuable. | **`/clr:pure`** |  |

Si vous liez votre programme à partir de la ligne de commande sans option de compilateur spécifiant une bibliothèque Runtime C, l’éditeur de liens utilise les bibliothèques CRT statiquement liées : *`libcmt.lib`* , *`libvcruntime.lib`* et *`libucrt.lib`* .

L'utilisation du CRT lié de manière statique implique que les informations d'état enregistrées par la bibliothèque runtime C sont locales pour cette instance du CRT. Par exemple, si vous utilisez [`strtok`](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) lors de l’utilisation d’un CRT lié de manière statique, la position de l' `strtok` analyseur n’est pas liée à l' `strtok` État utilisé dans le code du même processus (mais dans un autre fichier dll ou exe) qui est lié à une autre instance du CRT statique. En revanche, le CRT lié dynamiquement partage l'état pour tout le code dans un processus qui est lié dynamiquement au CRT. Cette restriction ne s'applique pas si vous utilisez les nouvelles versions plus sécurisées de ces fonctions ; par exemple, `strtok_s` n'a pas ce problème.

Comme une DLL générée avec une liaison à une bibliothèque CRT statique aura son propre état CRT, il est déconseillé de se lier statiquement à la bibliothèque CRT dans une DLL, sauf si les conséquences de cette action sont spécifiquement souhaitées et comprises. Par exemple, si vous appelez [`_set_se_translator`](../c-runtime-library/reference/set-se-translator.md) dans un exécutable qui charge la dll liée à sa propre bibliothèque CRT statique, les exceptions matérielles générées par le code dans la dll ne sont pas interceptées par le traducteur, mais les exceptions matérielles générées par le code dans l’exécutable principal sont interceptées.

Si vous utilisez le **`/clr`** commutateur du compilateur, votre code sera lié à une bibliothèque statique, msvcmrt. lib. La bibliothèque statique fournit un proxy entre votre code géré et la bibliothèque CRT native. Vous ne pouvez pas utiliser la bibliothèque CRT ( **`/MT`** ou les **`/MTd`** Options) liée de manière statique avec **`/clr`** . Utilisez à la place les bibliothèques liées dynamiquement ( **`/MD`** ou **`/MDd`** ). Les bibliothèques CRT managées pures sont déconseillées dans Visual Studio 2015 et non prises en charge dans Visual Studio 2017.

Pour plus d’informations sur l’utilisation de la bibliothèque CRT avec **`/clr`** , consultez [assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md).

Pour générer une version de débogage de votre application, l' [`_DEBUG`](../c-runtime-library/debug.md) indicateur doit être défini et l’application doit être liée à une version Debug de l’une de ces bibliothèques. Pour plus d'informations sur l'utilisation des versions Debug des fichiers de bibliothèques, consultez [Techniques de débogage de la bibliothèque CRT](/visualstudio/debugger/crt-debugging-techniques).

Cette version du CRT n’est pas entièrement conforme à la norme C99. Dans les versions antérieures à Visual Studio 2019 version 16,8, l' \<tgmath.h> en-tête n’est pas pris en charge. Dans toutes les versions, `CX_LIMITED_RANGE` les `FP_CONTRACT` macros et pragma ne sont pas prises en charge. Certains éléments tels que la signification des spécificateurs de paramètres dans les fonctions d’E/S standard utilisent des interprétations héritées par défaut. Vous pouvez utiliser **`/Zc`** les options de conformité du compilateur et spécifier les options de l’éditeur de liens pour contrôler certains aspects de la conformité de la bibliothèque.

## <a name="c-standard-library"></a>Bibliothèque standard C++

| Bibliothèque standard C++ | Caractéristiques | Option | Directives de préprocesseur |
|--|--|--|--|
| *`libcpmt.lib`* | Multithread, liaison statique | **`/MT`** | `_MT` |
| *`msvcprt.lib`* | Multithread, liaison dynamique (bibliothèque d’importation pour *`msvcp<version>.dll`* ) | **`/MD`** | `_MT`, `_DLL` |
| *`libcpmtd.lib`* | Multithread, liaison statique | **`/MTd`** | `_DEBUG`, `_MT` |
| *`msvcprtd.lib`* | Multithread, liaison dynamique (bibliothèque d’importation pour *`msvcp<version>d.dll`* ) | **`/MDd`** | `_DEBUG`, `_MT`, `_DLL` |

Lorsque vous générez une version Release de votre projet, une des bibliothèques Runtime C de base ( *`libcmt.lib`* , *`msvcmrt.lib`* , *`msvcrt.lib`* ) est liée par défaut, en fonction de l’option de compilateur choisie (multithread, dll, **`/clr`** ). Si vous incluez un des [fichiers d’en-tête de bibliothèque standard C++](../standard-library/cpp-standard-library-header-files.md) dans votre code, une bibliothèque standard C++ est liée automatiquement par Visual C++ au moment de la compilation. Par exemple :

```cpp
#include <ios>
```

Pour la compatibilité binaire, plusieurs fichiers DLL peuvent être spécifiés par une seule bibliothèque d’importation. Les mises à jour de version peuvent introduire des *bibliothèques dot*, des DLL séparées qui introduisent de nouvelles fonctionnalités de bibliothèque. Par exemple, Visual Studio 2017 version 15,6 introduite *`msvcp140_1.dll`* pour prendre en charge des fonctionnalités de bibliothèque standard supplémentaires sans rompre le Abi pris en charge par *`msvcp140.dll`* . La *`msvcprt.lib`* bibliothèque d’importation incluse dans l’ensemble d’outils pour Visual Studio 2017 version 15,6 prend en charge les deux dll et les vcredist pour cette version installent les deux dll. Une fois livrée, une bibliothèque dot a une ABI fixe et n’aura jamais de dépendance avec une bibliothèque dot ultérieure.

## <a name="what-problems-exist-if-an-application-uses-more-than-one-crt-version"></a>Quels sont les problèmes qui peuvent se poser si une application utilise plusieurs versions du CRT ?

Chaque image exécutable (EXE ou DLL) peut avoir son propre CRT lié statiquement, ou peut être liée de manière dynamique à un CRT. La version du CRT statique incluse ou chargée dynamiquement par une image particulière dépend de la version des outils et des bibliothèques avec lesquels elle a été créée. Un même processus peut charger plusieurs images EXE et DLL, chacune avec son propre CRT. Chacun de ces CRT peut utiliser un allocateur différent, avoir des dispositions de structure interne différentes, et utiliser des dispositions de stockage différentes. Cela signifie que la mémoire, les ressources CRT ou les classes allouées et passées dans une limite DLL peuvent entraîner des problèmes dans la gestion de la mémoire, dans l’utilisation statique interne ou dans interprétation de la disposition. Par exemple, si une classe est allouée dans une DLL, mais passée puis supprimée par une autre, quel est l’annulateur d’allocation CRT utilisé ? Les erreurs causées peuvent aller d’un léger problème à une erreur fatale irrécupérable et, par conséquent, le transfert direct de ces ressources est fortement déconseillé.

Vous pouvez éviter la plupart de ces problèmes en utilisant des technologies Application Binary Interface (ABI) car elles sont conçues pour être stables et versionnables. Concevez vos interfaces d’exportation DLL pour passer les informations par valeur ou pour utiliser une mémoire passée par l’appelant plutôt qu’allouée localement puis retournée à l’appelant. Utilisez des techniques de marshaling pour copier des données structurées entre des images exécutables. Encapsulez les ressources localement et autorisez uniquement la manipulation au moyen de handles ou de fonctions que vous exposez aux clients.

Il est également possible d’éviter certains de ces problèmes si toutes les images de votre processus utilisent la même version chargée dynamiquement du CRT. Pour vous assurer que tous les composants utilisent la même version DLL du CRT, générez-les à l’aide de l' **`/MD`** option et utilisez les mêmes ensemble d’outils de compilateur et paramètres de propriété.

Soyez prudent si votre programme passe certaines ressources CRT à travers les limites des DLL. Les ressources telles que les handles de fichiers, les paramètres régionaux et les variables d’environnement peuvent entraîner des problèmes, même si vous utilisez la même version du CRT. Pour plus d’informations sur les problèmes rencontrés et leur résolution, consultez [Erreurs potentielles de passage d’objets CRT entre frontières DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

## <a name="see-also"></a>Voir aussi

- [Référence de la bibliothèque Runtime C](../c-runtime-library/c-run-time-library-reference.md)

---
title: Avertissement des outils Éditeur de liens LNK4098
description: Décrit comment les bibliothèques incompatibles provoquent l’avertissement des outils de l’éditeur de liens LNK4098 et comment utiliser/NODEFAULTLIB pour le résoudre.
ms.date: 12/02/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 9d0c7da0614651a98d5ed4f3bd3676c7d837ce67
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74682946"
---
# <a name="linker-tools-warning-lnk4098"></a>Avertissement des outils Éditeur de liens LNK4098

> DEFAULTLIB'*Library*'est en conflit avec l’utilisation d’autres bibliothèques ; utilisez/NODEFAULTLIB :*Library*

Vous essayez de créer un lien avec des bibliothèques incompatibles.

> [!NOTE]
> Les bibliothèques Runtime contiennent désormais des directives pour empêcher le mélange de types différents. Vous recevrez cet avertissement si vous essayez d’utiliser des types différents ou des versions Debug et non Debug de la bibliothèque Runtime dans le même programme. Par exemple, si vous avez compilé un fichier pour utiliser un type de bibliothèque Runtime et un autre pour utiliser un autre type (par exemple, déboguer plutôt que commercial) et que vous avez tenté de les lier, vous obtiendrez cet avertissement. Vous devez compiler tous les fichiers sources pour utiliser la même bibliothèque Runtime. Pour plus d’informations, consultez les options de compilateur [/MD,/MT,/LD (utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md) .

Vous pouvez utiliser le commutateur [/Verbose : lib](../../build/reference/verbose-print-progress-messages.md) de l’éditeur de liens pour connaître les bibliothèques que l’éditeur de liens recherche. Par exemple, lorsque votre fichier exécutable utilise les bibliothèques Runtime non déboguées, la liste signalée doit inclure LIBCMT. lib et non LIBCMTD. lib, MSVCRT. lib ou MSVCRTD. lib. Vous pouvez demander à l’éditeur de liens d’ignorer les bibliothèques d’exécution incorrectes à l’aide de [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour chaque bibliothèque que vous souhaitez ignorer.

Le tableau ci-dessous indique les bibliothèques qui doivent être ignorées en fonction de la bibliothèque Runtime que vous souhaitez utiliser. Sur la ligne de commande, utilisez une option **/NODEFAULTLIB** pour chaque bibliothèque à ignorer. Dans l’IDE de Visual Studio, séparez les bibliothèques à ignorer par des points-virgules dans la propriété **Ignorer les bibliothèques par défaut spécifiques** .

| Pour utiliser cette bibliothèque Runtime | Ignorer ces bibliothèques |
|-----------------------------------|----------------------------|
| Multithread (LIBCMT. lib) | msvcrt. lib ; LIBCMTD. lib ; msvcrtd. lib |
| Multithread à l’aide de DLL (Msvcrt. lib) | LIBCMT. lib ; LIBCMTD. lib ; msvcrtd. lib |
| Débogage multithread (LIBCMTD. lib) | LIBCMT. lib ; msvcrt. lib ; msvcrtd. lib |
| Débogage multithread à l’aide de DLL (msvcrtd. lib) | LIBCMT. lib ; msvcrt. lib ; LIBCMTD. lib |

Par exemple, si vous avez reçu cet avertissement et que vous souhaitez créer un fichier exécutable qui utilise la version DLL de non-débogage des bibliothèques Runtime, vous pouvez utiliser les options suivantes avec l’éditeur de liens :

```cmd
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```

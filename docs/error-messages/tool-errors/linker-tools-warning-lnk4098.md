---
title: Avertissement des outils Éditeur de liens LNK4098
ms.date: 03/26/2019
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 66cf1a1bc75405ffc9bae8158bfc8682776a8228
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408093"
---
# <a name="linker-tools-warning-lnk4098"></a>Avertissement des outils Éditeur de liens LNK4098

> DEFAULTLIB '*bibliothèque*' est en conflit avec les autres bibliothèques ; utilisez/NODEFAULTLIB :*bibliothèque*

Que vous tentez de créer un lien avec des bibliothèques incompatibles.

> [!NOTE]
> Les bibliothèques Runtime contiennent maintenant des directives pour empêcher le mélange de types différents. Vous recevrez cet avertissement si vous tentez d’utiliser différents types et les versions sans débogage de la bibliothèque d’exécution dans le même programme. Par exemple, si vous avez compilé un fichier à utiliser un seul type de bibliothèque Runtime et un autre fichier à un autre type (par exemple, debug par rapport à la vente au détail) et tentez de les lier, vous obtiendrez cet avertissement. Vous devez compiler tous les fichiers source pour utiliser la même bibliothèque d’exécution. Pour plus d’informations, consultez le [/MD, / MT, /LD (utiliser la bibliothèque Runtime)](../../build/reference/md-mt-ld-use-run-time-library.md) options du compilateur.

Vous pouvez utiliser l’éditeur de liens [: lib](../../build/reference/verbose-print-progress-messages.md) commutateur pour connaître les bibliothèques que l’éditeur de liens recherche. Par exemple, lorsque votre fichier exécutable utilise les bibliothèques Runtime multithreads, sans débogage, la liste signalée doit inclure LIBCMT.lib et pas LIBCMTD.lib, MSVCRT.lib ou MSVCRTD.lib. Vous pouvez indiquer à l’éditeur de liens d’ignorer les bibliothèques d’exécution incorrects par le [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour chaque bibliothèque que vous souhaitez ignorer.

Le tableau ci-dessous présente les bibliothèques doivent être ignorées en fonction de la bibliothèque d’exécution que vous souhaitez utiliser. Sur la ligne de commande, utilisez une **/NODEFAULTLIB** option pour chacune des bibliothèques à ignorer. Dans l’IDE de Visual Studio, séparez les bibliothèques à ignorer par des points-virgules dans la **ignorer les bibliothèques par défaut spécifique** propriété.

| Pour utiliser cette bibliothèque d’exécution | Ignorer ces bibliothèques |
|-----------------------------------|----------------------------|
| Multithreaded (libcmt.lib) | msvcrt.lib; libcmtd.lib; msvcrtd.lib |
| Multithread utilisant des DLL (msvcrt.lib) | libcmt.lib; libcmtd.lib; msvcrtd.lib |
| Débogage multithread (libcmtd.lib) | libcmt.lib; msvcrt.lib; msvcrtd.lib |
| Débogage multithread utilisant des DLL (msvcrtd.lib) | libcmt.lib; msvcrt.lib; libcmtd.lib |

Par exemple, si vous avez reçu cet avertissement et que vous souhaitez créer un fichier exécutable qui utilise la version DLL non-debug, des bibliothèques Runtime, vous pouvez utiliser les options suivantes avec l’éditeur de liens :

```cmd
/NODEFAULTLIB:libcmt.lib NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
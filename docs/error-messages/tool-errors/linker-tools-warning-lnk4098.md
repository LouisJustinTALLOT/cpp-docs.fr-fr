---
title: Avertissement des outils Éditeur de liens LNK4098
ms.date: 11/04/2016
f1_keywords:
- LNK4098
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
ms.openlocfilehash: 088124fcce7cafad3fab3280ae0b3ae0d893283e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468716"
---
# <a name="linker-tools-warning-lnk4098"></a>Avertissement des outils Éditeur de liens LNK4098

conflit entre la 'library' utiliser et les autres bibliothèques ; utilisez/NODEFAULTLIB : library

Vous tentez de créer un lien avec des bibliothèques incompatibles.

> [!NOTE]
>  Les bibliothèques Runtime contiennent maintenant des directives pour empêcher le mélange de types différents. Vous recevrez cet avertissement si vous tentez d’utiliser différents types et les versions sans débogage de la bibliothèque d’exécution dans le même programme. Par exemple, si vous avez compilé un fichier pour un type d’exécution bibliothèque et un autre pour un autre type (par exemple, monothread et multithread) et a tenté de les lier, vous obtiendrez cet avertissement. Vous devez compiler tous les fichiers source pour utiliser la même bibliothèque d’exécution. Consultez le [utilisez Run-Time Library](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) les options du compilateur pour plus d’informations.

Vous pouvez utiliser l’éditeur de liens [: lib](../../build/reference/verbose-print-progress-messages.md) commutateur pour déterminer les bibliothèques dans l’éditeur de liens recherche. Si vous recevez LNK4098 et souhaitez créer un fichier exécutable qui utilise, par exemple, le thread unique, sans débogage bibliothèques Runtime, utilisez le **: lib** option afin de déterminer les bibliothèques que la recherche de l’éditeur de liens. L’éditeur de liens doit imprimer LIBC.lib et non LIBCMT.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib ou MSVCRTD.lib dans les bibliothèques recherchées. Vous pouvez indiquer à l’éditeur de liens d’ignorer les bibliothèques d’exécution incorrects par le [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour chaque bibliothèque que vous souhaitez ignorer.

Le tableau ci-dessous présente les bibliothèques doivent être ignorées en fonction de la bibliothèque d’exécution que vous souhaitez utiliser.

|Pour utiliser cette bibliothèque d’exécution|Ignorer ces bibliothèques|
|-----------------------------------|----------------------------|
|Thread unique (libc.lib)|LIBCMT.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Multithread (libcmt.lib)|libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Multithread utilisant des DLL (msvcrt.lib)|libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, msvcrtd.lib|
|Débogage monothread (libcd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, msvcrtd.lib|
|Débogage multithread (libcmtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, msvcrtd.lib|
|Débogage multithread utilisant des DLL (msvcrtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|

Par exemple, si vous avez reçu cet avertissement et que vous souhaitez créer un fichier exécutable qui utilise la version non debug, monothread, des bibliothèques Runtime, vous pouvez utiliser les options suivantes avec l’éditeur de liens :

```
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib
```
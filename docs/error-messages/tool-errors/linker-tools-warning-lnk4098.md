---
title: LNK4098 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4098
dev_langs:
- C++
helpviewer_keywords:
- LNK4098
ms.assetid: 1f1b1408-1316-4e34-80f5-6a02f2db0ac1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8aadf25d968d6d457f891cab49a43591455b9d12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301705"
---
# <a name="linker-tools-warning-lnk4098"></a>Avertissement des outils Éditeur de liens LNK4098
conflit entre 'library' à utiliser et les autres bibliothèques ; utilisez/NODEFAULTLIB : library  
  
 Vous tentez de créer un lien avec des bibliothèques incompatibles.  
  
> [!NOTE]
>  Les bibliothèques Runtime contiennent maintenant des directives pour empêcher le mélange de types différents. Vous recevez cet avertissement si vous tentez d’utiliser différents types et les versions sans débogage de la bibliothèque Runtime dans le même programme. Par exemple, si vous avez compilé un fichier pour une bibliothèque de type d’exécution et l’autre pour un autre type (par exemple, monothread ou multithread) et a tenté de les lier, vous obtenez cet avertissement. Vous devez compiler tous les fichiers sources pour utiliser la même bibliothèque d’exécution. Consultez le [utiliser la bibliothèque Runtime](../../build/reference/md-mt-ld-use-run-time-library.md) (**/MD**, **/MT**, **/LD**) les options du compilateur pour plus d’informations.  
  
 Vous pouvez utiliser l’éditeur de liens [: lib](../../build/reference/verbose-print-progress-messages.md) commutateur pour déterminer les bibliothèques dans l’éditeur de liens recherche. Si vous recevez LNK4098 et que vous souhaitez créer un fichier exécutable qui l’utilise, par exemple, le thread unique, non debug bibliothèques Runtime, utilisez le **: lib** option afin de déterminer les bibliothèques que l’éditeur de liens recherche. L’éditeur de liens doit imprimer LIBC.lib et non LIBCMT.lib, MSVCRT.lib, LIBCD.lib, LIBCMTD.lib ou MSVCRTD.lib dans les bibliothèques recherchées. Vous pouvez indiquer à ignorer les bibliothèques runtime incorrectes à l’aide de l’éditeur de liens [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour chaque bibliothèque que vous souhaitez ignorer.  
  
 Le tableau ci-dessous montre les bibliothèques doivent être ignorées en fonction de la bibliothèque Runtime dans laquelle vous souhaitez utiliser.  
  
|Pour utiliser cette bibliothèque Runtime|Ignorer ces bibliothèques|  
|-----------------------------------|----------------------------|  
|Thread unique (libc.lib)|LIBCMT.lib, msvcrt.lib, libcd.lib, libcmtd.lib, MSVCRTD.lib.|  
|Multithread (libcmt.lib)|libc.lib, msvcrt.lib, libcd.lib, libcmtd.lib, MSVCRTD.lib.|  
|Multithread utilisant des DLL (msvcrt.lib)|libc.lib, libcmt.lib, libcd.lib, libcmtd.lib, MSVCRTD.lib.|  
|Débogage monothread (libcd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcmtd.lib, MSVCRTD.lib.|  
|Débogage multithread (libcmtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, MSVCRTD.lib.|  
|Débogage multithread utilisant des DLL (msvcrtd.lib)|libc.lib, libcmt.lib, msvcrt.lib, libcd.lib, libcmtd.lib|  
  
 Par exemple, si vous avez reçu cet avertissement et que vous souhaitez créer un fichier exécutable qui utilise la version monothread sans débogage des bibliothèques Runtime, vous pouvez utiliser les options suivantes avec l’éditeur de liens :  
  
```  
/NODEFAULTLIB:libcmt.lib /NODEFAULTLIB:msvcrt.lib /NODEFAULTLIB:libcd.lib /NODEFAULTLIB:libcmtd.lib /NODEFAULTLIB:msvcrtd.lib  
```
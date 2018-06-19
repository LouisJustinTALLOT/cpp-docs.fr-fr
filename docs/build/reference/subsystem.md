---
title: -SUBSYSTEM | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c12df1a2166c9ef5a1af8a33a5764a8899909edb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377621"
---
# <a name="subsystem"></a>/SUBSYSTEM
Spécifie l’environnement d’exécution requis par l’image exécutable.  
  
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|  
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]  
```  
  
## <a name="remarks"></a>Notes  
 Cette option modifie l'image de façon à indiquer le sous-système que le système d'exploitation doit appeler pour l'exécution.  
  
 Vous pouvez spécifier l'un des sous-systèmes suivants :  
  
 BOOT_APPLICATION  
 Application qui s'exécute dans l'environnement de démarrage de Windows. Pour plus d’informations sur les applications de démarrage, consultez [à propos du fournisseur WMI BCD](http://msdn.microsoft.com/library/aa362639.aspx).  
  
 CONSOLE  
 Application en mode caractères de Windows. Le système d'exploitation fournit une console pour les applications console.  
  
 Image EFI (Extensible Firmware Interface)  
 Les options du sous-système EFI (Extensible Firmware Interface) décrivent les images exécutables qui s'exécutent dans l'environnement EFI. Cet environnement est généralement fourni avec le matériel et s'exécute avant que le système d'exploitation soit chargé. Les principales différences entre les types d'image EFI correspondent à l'emplacement de mémoire dans lequel l'image est chargée et l'action entreprise quand l'appel de l'image est retourné. Une image EFI_APPLICATION est déchargée quand le contrôle est retourné. Un EFI_BOOT_SERVICE_DRIVER ou un EFI_RUNTIME_DRIVER est déchargé uniquement si le contrôle est retourné avec un code d'erreur. Une image EFI_ROM est exécutée à partir de la mémoire ROM. Pour plus d’informations, consultez les spécifications sur le [Unified EFI Forum](http://www.uefi.org/) site Web.  
  
 NATIVE  
 Code qui s'exécute sans environnement de sous-système. Par exemple, des pilotes de périphérique en mode noyau et des processus système natifs. Cette option est généralement réservée aux fonctionnalités système de Windows.  
  
 POSIX  
 Application qui s'exécute dans le sous-système POSIX, dans Windows.  
  
 WINDOWS  
 Application qui s'exécute dans l'environnement graphique de Windows. Cela inclut les applications de bureau et applications de plateforme Windows universelle (UWP).  
  
 WINDOWSCE  
 Le sous-système WINDOWSCE indique que l'application est destinée à s'exécuter sur un périphérique doté d'une version du noyau Windows CE. Les versions du noyau incluent PocketPC, Windows Mobile, Windows Phone 7, Windows CE V1.0-6.0R3 et Windows Embedded Compact 7.  
  
 Les valeurs facultatives `major` et `minor` spécifient la version minimale requise du sous-système spécifié :  
  
-   La partie nombre entier du numéro de version, le segment à gauche du point décimal, est représentée par `major`.  
  
-   La partie fractionnelle du numéro de version (la partie à droite du point décimal) est représentée par `minor`.  
  
-   Les valeurs de `major` et `minor` doivent être comprises entre 0 et 65 535.  
  
 Le choix du sous-système affecte l'adresse de départ par défaut du programme. Pour plus d’informations, consultez [/ENTRY (symbole de Point d’entrée)](../../build/reference/entry-entry-point-symbol.md), l’éditeur de liens/ENTRY :*fonction* option.  
  
 Pour plus d’informations, y compris les valeurs minimales et par défaut pour les numéros de version majeure et mineure pour chaque sous-système, consultez le [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) option de l’éditeur de liens.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)
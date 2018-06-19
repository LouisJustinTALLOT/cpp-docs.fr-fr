---
title: 'Ressources localisées dans des Applications MFC : DLL satellites | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0740f567f17c8d44069211274ab1a4c66da311c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369115"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>Ressources localisées dans des applications MFC : DLL satellites
Version MFC 7.0 et versions ultérieure fournit la prise en charge améliorée pour les DLL satellites, une fonctionnalité qui vous aide à créer des applications localisées pour différentes langues. Un satellite DLL est un [DLL de ressource uniquement](../build/creating-a-resource-only-dll.md) qui contient les ressources localisées pour une langue particulière d’une application. Lorsque l’application commence à s’exécuter, MFC charge automatiquement la ressource localisée la plus appropriée pour l’environnement. Par exemple, vous pouvez avoir une application avec les ressources de langue anglaise avec deux DLL satellites, chacune contenant une traduction Français de vos ressources et l’autre contenant une traduction en allemand. Lorsque l’application est exécutée sur un système de langue anglaise, il utilise les ressources en anglais. Si vous exécutez sur un système Français, il utilise les ressources en Français ; Si vous exécutez sur un système en allemand, il utilise les ressources en allemand.  
  
 Pour prendre en charge des ressources localisées dans une application MFC, MFC tente de charger une DLL satellite contenant les ressources localisées pour une langue spécifique. Les DLL satellites sont nommées *NomApplicationXXX*.dll, où *ApplicationName* est le nom du .exe ou .dll à l’aide de MFC, et *XXX* est le code de trois lettres correspondant à la langue les ressources (par exemple, « ENU » ou « DEU »).  
  
 MFC tente de charger la DLL de ressource pour chacune des langues suivantes dans l’ordre, l’arrêt lorsqu’il détecte une :  
  
1. Par défaut langue d’interface utilisateur l’utilisateur actuel, tel que retourné par l’API Win32 GetUserDefaultUILanguage().  
  
2.  Langue d’interface utilisateur par défaut de l’utilisateur actuel, sans aucune sous-langue spécifique (c'est-à-dire, ENC [Canadian English] devient ENU [des États-Unis Anglais]).  
  
3.  La langue du système par défaut l’interface utilisateur, tel que retourné par l’API GetSystemDefaultUILanguage(). Sur d’autres plateformes, il s’agit de la langue du système d’exploitation lui-même.  
  
4.  La langue du système par défaut l’interface utilisateur, sans aucune sous-langue spécifique.  
  
5.  Une langue factice avec le code de 3 lettres LOC.  
  
 Si MFC ne trouve pas toutes les DLL satellites, il utilise les ressources contenues dans l’application elle-même.  
  
 Par exemple, supposons qu’une application LangExample.exe utilise MFC et s’exécute sur un système d’interface utilisateur multiples ; la langue de l’interface utilisateur du système est ENU [des États-Unis Anglais] et la langue de l’interface utilisateur de l’utilisateur actuel a la valeur FRC [Français canadien]. MFC recherche les DLL suivantes dans l’ordre suivant :  
  
1.  LangExampleFRC.dll (langue de l’interface utilisateur de l’utilisateur).  
  
2.  LangExampleFRA.dll (langue d’interface utilisateur de l’utilisateur sans sous-langue, dans cet exemple, Français (France).  
  
3.  LangExampleENU.dll (langue d’interface utilisateur du système).  
  
4.  LangExampleLOC.dll.  
  
 Si aucune de ces DLL n’est trouvée, MFC utilise les ressources contenues dans LangExample.exe.  
  
## <a name="see-also"></a>Voir aussi  
 [DLL en Visual C++](../build/dlls-in-visual-cpp.md)   
 [TN057 : localisation des composants MFC](../mfc/tn057-localization-of-mfc-components.md)
---
title: Types de DLL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 605d60535df8d0a94d58e120df89f975402b8a22
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369940"
---
# <a name="kinds-of-dlls"></a>Types de DLL
Cette rubrique fournit des informations pour vous aider à déterminer le type de DLL à générer.  
  
##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Différents types de DLL disponibles  
 À l’aide de Visual C++, vous pouvez générer des DLL Win32 en C ou C++ qui n’utilisent pas la bibliothèque Microsoft Foundation classes (MFC). Vous pouvez créer un projet de DLL non - MFC avec l’Assistant Application Win32.  
  
 La bibliothèque MFC elle-même est disponible, dans les deux bibliothèques de liens statiques ou dans un certain nombre de DLL, avec l’Assistant DLL MFC. Si votre DLL est à l’aide de MFC, Visual C++ prend en charge trois différents scénarios de développement de DLL :  
  
-   Génération d’une DLL MFC normale qui statiquement liée MFC  
  
-   Génération d’une DLL MFC normale qui dynamiquement liée à MFC  
  
-   Création d’une DLL d’extension MFC, qui toujours lier de manière dynamique MFC  
  
### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [DLL non-MFC : vue d’ensemble](../build/non-mfc-dlls-overview.md)  
  
-   [DLL MFC normales liées de manière statique aux MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [DLL MFC normales liées dynamiquement à MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [DLL d’extension de MFC : vue d’ensemble](../build/extension-dlls-overview.md)  
  
-   [Type de DLL à utiliser](#_core_which_kind_of_dll_to_use)  
  
##  <a name="_core_which_kind_of_dll_to_use"></a> Choix du type de DLL à utiliser  
 Si votre DLL n’utilise pas MFC, utilisez Visual C++ pour créer une DLL Win32 non - MFC. Liaison de la DLL de MFC (statiquement ou dynamiquement) occupe de la mémoire et espace disque important. Vous ne devez pas lier à MFC, sauf si votre DLL les utilise réellement.  
  
 Si votre DLL à l’aide MFC et sera utilisée par les applications MFC ou non-MFC, vous devez créer une DLL MFC normale liée de manière dynamique aux MFC ou une DLL MFC standard qui lie statiquement à MFC. Dans la plupart des cas, vous souhaiterez probablement utiliser une DLL MFC normale liée de manière dynamique aux MFC, car la taille du fichier de la DLL sera beaucoup plus petite et les gains en mémoire à partir de la version partagée de MFC peuvent être importantes. Si vous liez statiquement à MFC, la taille du fichier de votre DLL sera être plus volumineux et prendre la mémoire supplémentaire, car il charge sa propre copie privée du code de bibliothèque MFC.  
  
 Génération d’une DLL liée de manière dynamique aux MFC est plus rapide que la génération d’une DLL qui lie statiquement à MFC, car il n’est pas nécessaire de lier l’application MFC elle-même. Cela est particulièrement vrai dans les versions debug où l’éditeur de liens doit compacter les informations de débogage. En liaison avec une DLL qui contient déjà les informations de débogage, il est moins les informations de débogage à compacter dans la DLL.  
  
 L’un des inconvénients de la liaison dynamique aux MFC sont que vous devez distribuer les DLL partagées Mfcx0.dll et Msvcrxx.dll (ou des fichiers similaires) avec votre DLL. Les DLL MFC peuvent être redistribuées librement, mais vous devez toujours installer les DLL dans votre programme d’installation. En outre, vous devez expédier Msvcrxx.dll, qui contient la bibliothèque Runtime C qui est utilisée à la fois par votre programme et les DLL MFC elles-mêmes.  
  
 Si votre DLL ne doit pas être utilisée par des exécutables MFC, vous avez le choix entre la génération d’une DLL MFC normale ou une DLL d’extension MFC. Si la DLL implémente des classes réutilisables dérivées de classes MFC existantes, ou vous devez passer des objets dérivés des MFC entre l’application et la DLL, vous devez générer une DLL d’extension MFC.  
  
 Si votre DLL est liée dynamiquement à MFC, les DLL MFC peut être redistribués avec votre DLL. Cette architecture est particulièrement utile pour le partage de la bibliothèque de classes entre plusieurs fichiers exécutables pour économiser l’espace disque et de réduire l’utilisation de mémoire.  
  
 Avant la version 4.0, Visual C++ uniquement pris en charge deux types de DLL MFC : USRDLL et AFXDLL. DLL MFC normales liées de manière statique aux MFC ont les mêmes caractéristiques que l’ancienne USRDLL. DLL d’extension MFC ont les mêmes caractéristiques que l’ancienne AFXDLL.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [DLL non-MFC : vue d’ensemble](../build/non-mfc-dlls-overview.md)  
  
-   [DLL MFC normales liées de manière statique aux MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [DLL MFC normales liées dynamiquement à MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [DLL d’extension de MFC : vue d’ensemble](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DLL dans Visual C++](../build/dlls-in-visual-cpp.md)
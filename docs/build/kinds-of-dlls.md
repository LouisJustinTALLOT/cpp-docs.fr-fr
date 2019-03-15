---
title: Types de DLL
ms.date: 11/04/2016
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: f4aa8b1be7cd9ad32b10f12c5d1dfd3ae86adc1d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820284"
---
# <a name="kinds-of-dlls"></a>Types de DLL

Cette rubrique fournit des informations pour vous aider à déterminer le type de DLL à générer.

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Différents types de DLL disponibles

À l’aide de Visual C++, vous pouvez créer des DLL Win32 en C ou C++ qui n’utilisent pas la bibliothèque Microsoft Foundation classes (MFC). Vous pouvez créer un projet de DLL non - MFC avec l’Assistant Application Win32.

La bibliothèque MFC elle-même est disponible, dans les deux bibliothèques de liens statiques ou dans un certain nombre de DLL, avec l’Assistant DLL MFC. Si votre DLL est à l’aide de MFC, Visual C++ prend en charge trois différents scénarios de développement de DLL :

- Génération d’une DLL MFC normale qui statiquement liée de MFC

- Génération d’une DLL MFC normale qui dynamiquement liée à MFC

- Création d’une DLL d’extension MFC, qui toujours lier de manière dynamique MFC

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL non MFC : vue d’ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique aux MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : vue d’ensemble](extension-dlls-overview.md)

- [Type de DLL à utiliser](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> Choix du type de DLL à utiliser

Si votre DLL n’utilise pas MFC, utilisez Visual C++ pour générer une DLL Win32 non - MFC. Liaison de la DLL aux MFC (statiquement ou dynamiquement) occupe de la mémoire et espace disque important. Vous ne devez pas lier à MFC, sauf si votre DLL les utilise réellement.

Si votre DLL à l’aide MFC et sera utilisée par des applications MFC ou non-MFC, vous devez générer une DLL MFC normale liée de manière dynamique aux MFC ou une DLL MFC normale liée de manière statique aux MFC. Dans la plupart des cas, vous souhaiterez probablement utiliser une DLL MFC normale liée de manière dynamique aux MFC car la taille du fichier de la DLL sera beaucoup plus petite et les économies dans la mémoire à l’aide de la version partagée des MFC peuvent être significatifs. Si vous liez statiquement à MFC, la taille du fichier de votre DLL sera être plus grande et occupera mémoire supplémentaire car elle chargera sa propre copie privée du code de bibliothèque MFC.

Génération d’une DLL liée de manière dynamique aux MFC est plus rapide que la génération d’une DLL liée de manière statique aux MFC car il n’est pas nécessaire de lier l’application MFC elle-même. Cela est particulièrement vrai dans les versions debug où l’éditeur de liens doit compacter les informations de débogage. En liant avec une DLL qui contient déjà les informations de débogage, il est moins les informations de débogage à compacter dans votre DLL.

L’un des inconvénients de la liaison dynamique aux MFC sont que vous devez distribuer les DLL partagées Mfcx0.dll et Msvcrxx.dll (ou des fichiers similaires) avec votre DLL. Les DLL MFC peuvent être redistribuées librement, mais vous devez toujours installer les DLL dans votre programme d’installation. En outre, vous devez expédier Msvcrxx.dll, qui contient la bibliothèque Runtime C qui est utilisée par votre programme et les DLL MFC elles-mêmes.

Si votre DLL ne doit pas être utilisée par des exécutables MFC, vous avez le choix entre la génération d’une DLL MFC normale ou une DLL d’extension MFC. Si la DLL implémente des classes réutilisables dérivées de classes MFC existantes, ou vous devez passer des objets dérivés des MFC entre l’application et la DLL, vous devez générer une DLL d’extension MFC.

Si votre DLL liée de manière dynamique aux MFC, les DLL MFC peuvent être redistribués avec votre DLL. Cette architecture est particulièrement utile pour le partage de la bibliothèque de classes entre plusieurs fichiers exécutables afin d’économiser l’espace disque et de réduire l’utilisation de la mémoire.

Avant la version 4.0, Visual C++ prises uniquement en charge deux types de DLL MFC : USRDLL et AFXDLL. DLL MFC normales liées de manière statique aux MFC ont les mêmes caractéristiques que l’ancienne USRDLL. DLL d’extension MFC ont les mêmes caractéristiques que l’ancienne AFXDLL.

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL non MFC : vue d’ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique aux MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique aux MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : vue d’ensemble](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](dlls-in-visual-cpp.md)

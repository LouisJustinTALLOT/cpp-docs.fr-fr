---
description: 'En savoir plus sur : genres de dll'
title: Types de DLL
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: 284881d9091791038c547914887275ee02605156
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156136"
---
# <a name="kinds-of-dlls"></a>Types de DLL

Cette rubrique fournit des informations pour vous aider à déterminer le type de DLL à générer.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Différents types de dll disponibles

À l’aide de Visual Studio, vous pouvez générer des dll Win32 en C ou C++ qui n’utilisent pas la bibliothèque MFC (Microsoft Foundation Class). Vous pouvez créer un projet de DLL non-MFC à l’aide de l’Assistant application Win32.

La bibliothèque MFC elle-même est disponible, soit dans les bibliothèques de liens statiques, soit dans un certain nombre de dll, avec l’Assistant DLL MFC. Si votre DLL utilise MFC, Visual Studio prend en charge trois scénarios de développement de DLL différents :

- Génération d’une DLL MFC normale qui lie statiquement les MFC

- Génération d’une DLL MFC normale qui lie dynamiquement MFC

- Génération d’une DLL d’extension MFC, qui est toujours liée de manière dynamique aux MFC

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL non MFC : Vue d'ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : Vue d'ensemble](extension-dlls-overview.md)

- [Le type de DLL à utiliser](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a> Choix du type de DLL à utiliser

Si votre DLL n’utilise pas MFC, utilisez Visual Studio pour générer une DLL Win32 non MFC. Le fait de lier votre DLL à MFC (de manière statique ou dynamique) nécessite un espace disque et une mémoire significatifs. Vous ne devez pas établir de liaison avec MFC à moins que votre DLL utilise réellement MFC.

Si votre DLL utilise MFC et qu’elle est utilisée par des applications MFC ou non-MFC, vous devez générer une DLL MFC normale qui est liée de manière dynamique aux MFC ou à une DLL MFC normale qui est liée de manière statique aux MFC. Dans la plupart des cas, vous souhaiterez probablement utiliser une DLL MFC standard liée de manière dynamique aux MFC, car la taille de fichier de la DLL sera beaucoup plus petite et les économies en mémoire de l’utilisation de la version partagée de MFC peuvent être importantes. Si vous établissez une liaison statique avec MFC, la taille du fichier de votre DLL sera plus grande et pourrait potentiellement occuper de la mémoire supplémentaire, car elle charge sa propre copie privée du code de la bibliothèque MFC.

La génération d’une DLL liée de manière dynamique aux MFC est plus rapide que la génération d’une DLL liée de manière statique aux MFC, car il n’est pas nécessaire de lier MFC elle-même. Cela est particulièrement vrai dans les versions Debug où l’éditeur de liens doit compacter les informations de débogage. En établissant une liaison avec une DLL qui contient déjà les informations de débogage, il y a moins d’informations de débogage à compacter dans votre DLL.

L’un des inconvénients de la liaison dynamique avec MFC est que vous devez distribuer les DLL partagées Mfcx0.dll et Msvcrxx.dll (ou des fichiers similaires) avec votre DLL. Les DLL MFC sont librement redistribuables, mais vous devez toujours installer les dll dans votre programme d’installation. En outre, vous devez expédier le Msvcrxx.dll, qui contient la bibliothèque Runtime C qui est utilisée à la fois par votre programme et les DLL MFC elles-mêmes.

Si votre DLL est utilisée uniquement par les exécutables MFC, vous avez le choix entre générer une DLL MFC normale ou une DLL d’extension MFC. Si votre DLL implémente des classes réutilisables dérivées des classes MFC existantes ou si vous devez passer des objets dérivés de MFC entre l’application et la DLL, vous devez générer une DLL d’extension MFC.

Si votre DLL est liée de manière dynamique aux MFC, les DLL MFC peuvent être redistribuées avec votre DLL. Cette architecture est particulièrement utile pour le partage de la bibliothèque de classes entre plusieurs fichiers exécutables afin d’économiser de l’espace disque et de réduire l’utilisation de la mémoire.

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL non MFC : Vue d'ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : Vue d'ensemble](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)

---
title: Types de DLL
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328500"
---
# <a name="kinds-of-dlls"></a>Types de DLL

Ce sujet fournit des informations pour vous aider à déterminer le type de DLL à construire.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>Différents types de DLLs disponibles

À l’aide de Visual Studio, vous pouvez créer des reflex win32 en C ou en CMD qui n’utilisent pas la bibliothèque Microsoft Foundation Class (MFC). Vous pouvez créer un projet DLL non-MFC avec l’Assistant d’Application Win32.

La bibliothèque MFC elle-même est disponible, soit dans les bibliothèques de liaisons statiques, soit dans un certain nombre de DLL, avec le MFC DLL Wizard. Si votre DLL utilise MFC, Visual Studio prend en charge trois scénarios de développement DLL différents :

- Construire un DLL MFC régulier qui relie statiquement MFC

- Construire un DLL MFC régulier qui relie dynamiquement MFC

- Construire une extension MFC DLL, qui relie toujours dynamiquement MFC

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL non-MFC : vue d’ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : vue d’ensemble](extension-dlls-overview.md)

- [Quel genre de DLL utiliser](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Décider quel type de DLL utiliser

Si votre DLL n’utilise pas MFC, utilisez Visual Studio pour construire un DLL Win32 non-MFC. Lier votre DLL à MFC (statiquement ou dynamiquement) prend l’espace et la mémoire de disque significatifs. Vous ne devez pas vous connecter à MFC à moins que votre DLL utilise réellement MFC.

Si votre DLL utilise MFC, et sera utilisé par des applications MFC ou non-MFC, vous devez construire soit un DLL MFC régulier qui relie dynamiquement à MFC ou un DLL MFC régulier qui relie statiquement à MFC. Dans la plupart des cas, vous voulez probablement utiliser un DLL MFC régulier qui relie dynamiquement à MFC parce que la taille du fichier de la DLL sera beaucoup plus petite et les économies de mémoire de l’utilisation de la version partagée de MFC peut être significative. Si vous êtes relié statiquement à MFC, la taille du fichier de votre DLL sera plus grande et potentiellement prendre la mémoire supplémentaire parce qu’il charge sa propre copie privée du code de bibliothèque MFC.

Construire un DLL qui relie dynamiquement à MFC est plus rapide que la construction d’un DLL qui relie statiquement à MFC parce qu’il n’est pas nécessaire de lier MFC lui-même. Cela est particulièrement vrai dans les constructions de débog où le lien doit compacter l’information de débogé. En établissant un lien avec un DLL qui contient déjà les informations de débog, il ya moins d’informations débbug à compacter dans votre DLL.

Un inconvénient à l’établissement d’un lien dynamique vers MFC est que vous devez distribuer les DLL Mfcx.dll et Msvcrxx.dll (ou fichiers similaires) avec votre DLL. Les DLL MFC sont librement redistributables, mais vous devez toujours installer les DLL dans votre programme d’installation. De plus, vous devez expédier le Msvcrxx.dll, qui contient la bibliothèque C run-time qui est utilisée à la fois par votre programme et les LGN MFC eux-mêmes.

Si votre DLL ne sera utilisé que par les exécutables MFC, vous avez le choix entre la construction d’un DLL MFC régulier ou une extension MFC DLL. Si votre DLL implémente des classes réutilisables issues des classes MFC existantes ou si vous devez passer des objets dérivés du MFC entre l’application et le DLL, vous devez construire une DLL d’extension MFC.

Si votre DLL est relié dynamiquement à MFC, les LGN MFC peuvent être redistribués avec votre DLL. Cette architecture est particulièrement utile pour partager la bibliothèque de classe entre plusieurs fichiers exécutables pour économiser de l’espace disque et minimiser l’utilisation de la mémoire.

### <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

- [DLL non-MFC : vue d’ensemble](non-mfc-dlls-overview.md)

- [DLL MFC normales liées de manière statique à MFC](regular-dlls-statically-linked-to-mfc.md)

- [DLL MFC normales liées de manière dynamique à MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [DLL d’extension de MFC : vue d’ensemble](extension-dlls-overview.md)

## <a name="see-also"></a>Voir aussi

[Création de DLL C/C++ dans Visual Studio](dlls-in-visual-cpp.md)

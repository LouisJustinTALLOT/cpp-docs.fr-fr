---
title: 'DLL d’extension : Vue d’ensemble de | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bd851b9335e2b1ecffc8873590f176d7ebb2205
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367818"
---
# <a name="mfc-extension-dlls-overview"></a>DLL d’extension MFC : vue d’ensemble
Une extension MFC DLL est une DLL qui implémentent généralement des classes réutilisables dérivées de classes Microsoft Foundation Class Library existantes. DLL d’extension MFC sont générées à l’aide de la version de la bibliothèque de liens dynamiques des MFC (également appelée la version partagée de MFC). Uniquement exécutables MFC (applications ou des DLL MFC standard) qui sont générés avec la version partagée de MFC peuvent utiliser une DLL d’extension MFC. Avec une DLL d’extension MFC, vous pouvez dériver de nouvelles classes personnalisées à partir de MFC et puis offrir cette version étendue des MFC pour les applications qui appellent votre DLL.  
  
 DLL d’extension peuvent également servir pour passer des objets dérivés des MFC entre l’application et la DLL. Les fonctions membres associées à l’objet passé existent dans le module où l’objet a été créé. Étant donné que ces fonctions sont exportées correctement lorsque vous utilisez la version DLL partagée de MFC, vous pouvez passer librement MFC ou des pointeurs d’objet dérivé des MFC entre une application et la chargement de DLL d’extension MFC.  
  
 Pour obtenir un exemple d’une DLL qui répondent aux critères de base d’une DLL d’extension MFC, consultez l’exemple MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). En particulier, examinez les fichiers Testdll1.cpp et Testdll2.cpp.  
  
 Notez que le terme AFXDLL n’est plus utilisé dans la documentation Visual C++. Une DLL d’extension MFC a les mêmes caractéristiques que l’ancienne AFXDLL.  
  
## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?  
  
-   [Initialiser une DLL d’extension MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
  
-   [DLL d’extension de MFC](../build/extension-dlls.md)  
  
-   [Utilisation de DLL d’extension de MFC de type base de données, OLE et sockets dans des DLL MFC normales](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [DLL non-MFC : vue d’ensemble](../build/non-mfc-dlls-overview.md)  
  
-   [DLL MFC normales liées de manière statique aux MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [DLL MFC normales liées dynamiquement à MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Création d’une DLL MFC](../mfc/reference/mfc-dll-wizard.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Genres de DLL](../build/kinds-of-dlls.md)
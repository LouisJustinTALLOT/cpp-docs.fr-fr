---
title: Création d’une DLL de ressource uniquement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5249f4528038771162bb96b714524ed751ff39a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367545"
---
# <a name="creating-a-resource-only-dll"></a>Création d'une DLL de ressource uniquement  
  
Une DLL de ressource uniquement est une DLL qui ne contient que des ressources, telles que des icônes, des bitmaps, des chaînes et des boîtes de dialogue. À l’aide d’une DLL de ressource uniquement est un bon moyen de partager le même jeu de ressources entre plusieurs programmes. Il est également une bonne solution pour fournir une application de ressources localisées pour plusieurs langues (consultez [des ressources localisées dans des Applications MFC : DLL satellites](../build/localized-resources-in-mfc-applications-satellite-dlls.md)).  
  
Pour créer une DLL de ressource uniquement, vous créez un nouveau projet de DLL de Win32 (non-MFC) et ajoutez vos ressources au projet.  
  
-   Sélectionnez projet Win32 dans le **nouveau projet** boîte de dialogue zone, puis spécifiez un type de projet DLL dans l’Assistant Projet Win32.  
  
-   Créer un nouveau script de ressources qui contient les ressources (par exemple, une chaîne ou un menu) pour la DLL et enregistrez le fichier .rc.  
  
-   Sur le **projet** menu, cliquez sur **ajouter un élément existant**, puis insérez le nouveau fichier .rc dans le projet.  
  
-   Spécifiez le [/NOENTRY](../build/reference/noentry-no-entry-point.md) option de l’éditeur de liens. /NOENTRY empêche l’éditeur de liens de lier une référence à `_main` dans la DLL ; cette option est requise pour créer une DLL de ressource uniquement.  
  
-   Créez la DLL.  
  
L’application qui utilise la DLL de ressource uniquement doit appeler [LoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) pour une liaison explicite à la DLL. Pour accéder aux ressources, appelez les fonctions génériques `FindResource` et `LoadResource`, qui fonctionnent sur n’importe quel type de ressource, ou que vous appelez l’une des fonctions spécifiques aux ressources suivantes :  
  
-   `FormatMessage`  
  
-   `LoadAccelerators`  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
L’application doit appeler `FreeLibrary` quand elle est terminée en utilisant les ressources.  
  
## <a name="see-also"></a>Voir aussi  
  
[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)  
[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)
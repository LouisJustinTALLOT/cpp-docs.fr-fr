---
title: "Modifications apportées à la DLL du chargement différé fonction d’assistance depuis Visual C++ 6.0 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, what's changed
- PFromRva method
- __delayLoadHelper2 function
- helper functions, what's changed
ms.assetid: 99f0be69-105d-49ba-8dd5-3be7939c0c72
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fb16beb6f2ddb07f57fe9f35c67552348cac56cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="changes-in-the-dll-delayed-loading-helper-function-since-visual-c-60"></a>Modifications apportées à la fonction d'assistance du chargement différé des DLL depuis Visual C++ 6.0
Si vous avez plusieurs versions de Visual C++ sur votre ordinateur ou si vous avez défini votre propre fonction d’assistance, vous pouvez être affecté par les modifications apportées à la DLL de fonction d’assistance de chargement différé. Exemple :  
  
-   **__delayLoadHelper** est désormais **__delayLoadHelper2**  
  
-   **__pfnDliNotifyHook** est désormais **__pfnDliNotifyHook2**  
  
-   **__pfnDliFailureHook** est désormais **__pfnDliFailureHook2**  
  
-   **__FUnloadDelayLoadedDLL** est désormais **__FUnloadDelayLoadedDLL2**  
  
> [!NOTE]
>  Si vous utilisez la fonction d’assistance par défaut, ces modifications ne vous concernent pas. Il n’y a aucune modification en ce qui concerne la façon dont vous appelez l’éditeur de liens.  
  
## <a name="multiple-versions-of-visual-c"></a>Plusieurs Versions de Visual C++  
 Si vous avez plusieurs versions de Visual C++ sur votre ordinateur, assurez-vous que l’éditeur de liens correspond à delayimp.lib. S’il existe une incompatibilité, vous obtiendrez une erreur de l’éditeur de liens signalant `___delayLoadHelper2@8` ou `___delayLoadHelper@8` comme un symbole externe non résolu. La première implique un nouvel éditeur de liens avec une ancienne bibliothèque delayimp.lib, et cette dernière implique un éditeur de liens ancien avec une nouvelle bibliothèque delayimp.lib.  
  
 Si vous obtenez une erreur de l’éditeur de liens non résolue, exécutez [dumpbin /linkermember](../../build/reference/linkermember.md): 1 sur la bibliothèque delayimp.lib susceptible de contenir la fonction d’assistance pour savoir quelle est la fonction d’assistance est définie à la place. La fonction d’assistance peut également être définie dans un fichier objet ; Exécutez [dumpbin /symbols](../../build/reference/symbols.md) et recherchez `delayLoadHelper(2)`.  
  
 Si vous connaissez l’éditeur de liens Visual C++ 6.0, puis :  
  
-   Exécutez dumpbin dans le fichier .lib ou .obj de l’assistance chargement différé pour savoir si elle définit **__delayLoadHelper2**. Si ce n’est pas le cas, la liaison échoue.  
  
-   Définir **__delayLoadHelper** dans le délai de charger le fichier .lib ou .obj de l’Assistant.  
  
## <a name="user-defined-helper-function"></a>Fonction d’assistance de défini par l’utilisateur  
 Si vous défini votre propre fonction d’assistance et que vous utilisez la version actuelle de Visual C++, procédez comme suit :  
  
-   Renommez la fonction d’assistance **__delayLoadHelper2**.  
  
-   Étant donné que les pointeurs du descripteur de différé (ImgDelayDescr dans delayimp.h) ont été modifiés à partir d’adresses absolues (va) pour les adresses relatives (RVA) de fonctionner comme prévu dans les deux programmes 32 et 64 bits, vous devez les reconvertir en pointeurs. Une nouvelle fonction a été introduite : PFromRva, située dans delayhlp.cpp. Vous pouvez utiliser cette fonction sur chacun des champs du descripteur pour les convertir en pointeurs 32 ou 64 bits. La fonction de d’assistance de chargement différé par défaut reste un bon modèle à utiliser comme exemple.  
  
## <a name="load-all-imports-for-a-delay-loaded-dll"></a>Charger toutes les importations pour une DLL à chargement différé  
 L’éditeur de liens peut charger toutes les importations d’une DLL que vous avez spécifié pour le chargement différé. Consultez [le chargement de toutes les importations pour une DLL à chargement différé](../../build/reference/loading-all-imports-for-a-delay-loaded-dll.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la fonction d’assistance](understanding-the-helper-function.md)
---
title: Erreur d’exécution de C R6033 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6033
dev_langs:
- C++
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed66dec4f4eb17378c9901439be2ad1449597a93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299992"
---
# <a name="c-runtime-error-r6033"></a>Erreur d’exécution de C R6033
Essayez d’utiliser le code MSIL de cet assembly lors de l’initialisation du code natif. Cela indique un bogue dans votre application. Il est très probablement le résultat de l’appel à un MSIL compilé (/ clr) à partir d’un constructeur natif ou de DllMain (fonction).  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Cette erreur peut être provoquée par un bogue dans l’application, ou par un bogue dans un complément ou une extension qu’il utilise.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** supprimer, réparer ou réinstaller les extensions ou les compléments.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Ce diagnostic indique que des instructions MSIL s’exécutaient lors du verrouillage du chargeur. Cela peut se produire si vous avez compilé le code C++ natif à l’aide de l’indicateur/CLR. Utilisez uniquement l’indicateur/CLR sur les modules qui contiennent du code managé. Pour plus d’informations, consultez [l’initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md).
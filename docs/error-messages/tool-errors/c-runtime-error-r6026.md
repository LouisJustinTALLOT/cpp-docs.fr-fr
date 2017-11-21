---
title: "R6026 d’erreur d’exécution C | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6026
dev_langs: C++
helpviewer_keywords: R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4a7d39d0ec4dd71b835c39c4a600154be7f206da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6026"></a>R6026 d’erreur d’exécution C
pas assez d’espace pour l’initialisation de stdio  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons possibles de cette erreur, mais il est généralement causé par une condition de mémoire. Il peut également être provoqué par un bogue dans l’application, par l’altération des bibliothèques Visual C++ qu’il utilise ou par un pilote.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Si l’application fonctionnait avant une installation récente d’une autre application ou le pilote, utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour supprimer le nouvelle application ou le pilote, puis réessayez votre application.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller toutes les copies de Microsoft Visual C++ Redistributable.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Cette erreur se produit lorsqu’il n’est pas suffisamment de mémoire disponible pour initialiser la prise en charge d’e/s standard dans le runtime C. Cette erreur se produit généralement lors du démarrage de l’application. Vérifiez que votre application et les DLL qu’il charge et les pilotes de ne pas endommager le tas au démarrage.
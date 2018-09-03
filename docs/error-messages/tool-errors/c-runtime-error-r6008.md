---
title: R6008 d’erreur d’exécution C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d32734850c58b64694e96c3a27b759131e6c5ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299875"
---
# <a name="c-runtime-error-r6008"></a>R6008 d’erreur d’exécution C
pas assez d’espace pour les arguments  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons possibles de cette erreur, mais il est souvent dû à une condition de mémoire faible, trop de mémoire consommée par les variables d’environnement ou un bogue dans le programme.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.  
> -   Réduire le nombre et la taille des arguments de ligne de commande à l’application.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Il a été suffisamment de mémoire pour charger le programme, mais pas assez de mémoire pour créer la **argv** tableau. Cela peut être dû en conditions de mémoire ou en exceptionnellement élevé de lignes de commande ou l’utilisation de variables d’environnement. Considérez l’une des solutions suivantes :  
  
-   Augmentez la quantité de mémoire disponible pour le programme.  
  
-   Réduire le nombre et la taille des arguments de ligne de commande.  
  
-   Réduire la taille de l’environnement en supprimant les variables superflues.
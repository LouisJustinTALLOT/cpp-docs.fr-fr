---
title: R6028 d’erreur d’exécution C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b978d1d9165fd48be9d0ce31aa72092fc660dbd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297821"
---
# <a name="c-runtime-error-r6028"></a>R6028 d’erreur d’exécution C
impossible d'initialiser le tas  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème de mémoire interne. Il existe plusieurs raisons à cette erreur, mais souvent, elle est provoquée par une condition de mémoire, un bogue dans le programme, ou par les pilotes matériels défectueux.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Fermez les autres applications en cours d’exécution ou redémarrer votre ordinateur pour libérer la mémoire.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Si l’application fonctionnait avant une installation récente d’une autre application ou le pilote, utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour supprimer le nouvelle application ou le pilote, puis réessayez votre application.  
> -   Consultez le site Web du fabricant de votre matériel ou **mise à jour Windows** dans les **le panneau de configuration** des mises à jour de logiciel et le pilote.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Cette erreur se produit lorsque le système d'exploitation ne parvient pas à créer le pool de mémoire pour l'application ; plus particulièrement, CRT (C Runtime) a appelé la fonction Win32 `HeapCreate`, qui a retourné la valeur NULL, ce qui indique un échec.  
  
 Si cette erreur se produit au démarrage de l'application, le système n'est peut-être pas en mesure de répondre aux requêtes de tas, en raison du chargement de pilotes défectueux. Consultez le site Web Windows Update ou le site Web du fabricant de votre matériel pour obtenir des pilotes mis à jour.
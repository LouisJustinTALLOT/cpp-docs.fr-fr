---
title: R6019 d’erreur d’exécution C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95950254d4a0611d9690b8636eb50f2fc1f0f264
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314227"
---
# <a name="c-runtime-error-r6019"></a>R6019 d’erreur d’exécution C
Impossible d’ouvrir le périphérique de la console  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a tenté d’accéder à la console, mais il ne dispose pas des autorisations suffisantes. Il existe plusieurs raisons possibles de cette erreur, mais il est généralement parce que le programme doit s’exécuter en tant qu’administrateur, ou il existe un bogue dans le programme.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Exécutez le programme en tant qu’administrateur.  
> -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Cette erreur se produit parce que l’application a appelé une fonction de la console, mais le système d’exploitation n’a pas accordé l’accès à la console. Sauf en mode débogage, fonctions de la console sont généralement pas autorisées dans les applications Microsoft Store. Si votre application nécessite des privilèges d’administrateur pour exécuter, vérifiez qu’il est installé pour s’exécuter en tant qu’administrateur par défaut.
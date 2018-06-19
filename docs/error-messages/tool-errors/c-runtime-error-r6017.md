---
title: R6017 d’erreur d’exécution C | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f726f1e01acc20899085f8f1b84f74265843bbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302722"
---
# <a name="c-runtime-error-r6017"></a>R6017 d’erreur d’exécution C
Erreur de verrouillage multithread inattendue  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Il existe plusieurs raisons possibles de cette erreur, mais souvent, elle est provoquée par un défaut dans le code de l’application.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Le processus a reçu une erreur inattendue lors de la tentative d’accéder à un verrou multithread d’exécution C sur une ressource système. Cette erreur se produit généralement quand le processus modifie par inadvertance les données de segment de mémoire du runtime. Cependant, il peut également être dû à une erreur interne dans la bibliothèque runtime ou le code du système d’exploitation.  
  
 Pour résoudre ce problème, recherchez les bogues d’altération du tas dans votre code. Pour plus d’informations et d’exemples, consultez [détails du tas de débogage CRT](/visualstudio/debugger/crt-debug-heap-details). Ensuite, vérifiez que vous utilisez les derniers redistribuables pour votre déploiement d’application. Pour plus d’informations, consultez [déploiement dans Visual C++](../../ide/deployment-in-visual-cpp.md).
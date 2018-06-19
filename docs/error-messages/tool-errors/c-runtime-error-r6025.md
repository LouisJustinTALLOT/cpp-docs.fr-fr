---
title: Erreur d’exécution C R6025 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6025
dev_langs:
- C++
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: abdbdbf918462dfb83eff07190c32af1f1b3d015
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302024"
---
# <a name="c-runtime-error-r6025"></a>Erreur d’exécution C R6025
appel de fonction virtuelle pure  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. La raison la plus courante de cette erreur est un bogue dans l’application ou d’une installation endommagée.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Aucun objet n’a été instancié pour gérer l’appel de fonction virtuelle pure.  
  
 Cette erreur est due en appelant une fonction virtuelle dans une classe de base abstraite via un pointeur qui est créé par un cast vers le type de la classe dérivée, mais est en fait un pointeur vers la classe de base. Cela peut se produire lors de la conversion d’un **void\***  vers un pointeur vers une classe lorsque le **void\***  a été créé pendant la construction de la classe de base.  
  
 Pour plus d’informations, consultez la [prise en charge Microsoft](http://go.microsoft.com/fwlink/p/?linkid=75220) site Web.
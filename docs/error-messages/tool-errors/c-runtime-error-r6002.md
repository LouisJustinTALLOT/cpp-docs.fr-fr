---
title: Erreur d’exécution C R6002 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6002
dev_langs:
- C++
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a970ecea4fdd7d397c09672b0548be947cab1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298562"
---
# <a name="c-runtime-error-r6002"></a>Erreur d’exécution C R6002
prise en charge de virgule flottante n’a ne pas chargé  
  
 La bibliothèque à virgule flottante nécessaire n’était pas liée.  
  
> [!NOTE]
>  Si vous rencontrez ce message d’erreur lors de l’exécution d’une application, l’application a été arrêtée, car il a un problème interne. Il existe plusieurs raisons possibles de cette erreur, mais souvent, elle est provoquée par un défaut dans le code de l’application, ou en essayant d’exécuter une application qui n’a pas été générée pour le processeur de votre ordinateur particulier.  
>   
>  Vous pouvez essayer de suivre les étapes ci-après pour corriger cette erreur :  
>   
>  -   Utilisez le **applications et fonctionnalités** ou **programmes et fonctionnalités** page dans le **le panneau de configuration** pour réparer ou réinstaller le programme.  
> -   Vérifiez **mise à jour Windows** dans les **le panneau de configuration** pour les mises à jour logicielles.  
> -   Recherchez une version mise à jour de l’application. Si le problème persiste, contactez le fournisseur de l’application.  
  
 **Informations pour les programmeurs**  
  
 Cette erreur peut se produire dans votre application lors de la bibliothèque à virgule flottante n’était pas liée. Recherchez une de ces causes :  
  
-   Une chaîne de format pour un `printf_s` ou `scanf_s` fonction contenait une spécification de format à virgule flottante et le programme ne contenait pas les valeurs à virgule flottante ou les variables. Pour résoudre ce problème, utilisez un argument à virgule flottante pour correspondre à la spécification de format à virgule flottante, ou procédez à une assignation à virgule flottante ailleurs dans le programme. Cela provoque une prise en charge à virgule flottante doit être chargé.  
  
-   Le compilateur réduit la taille d’un programme en chargeant une prise en charge à virgule flottante uniquement lorsque cela est nécessaire. Le compilateur ne peut pas détecter les opérations à virgule flottante ou des spécifications de format à virgule flottante dans les chaînes de format, afin qu’il ne charge pas les routines à virgule flottante nécessaires. Pour résoudre ce problème, utilisez une spécification de format à virgule flottante et fournissez un argument à virgule flottante ou procédez à une assignation à virgule flottante ailleurs dans le programme. Cela provoque une prise en charge à virgule flottante doit être chargé.  
  
-   Dans un programme à plusieurs langages, une bibliothèque C a été spécifiée avant une bibliothèque FORTRAN lorsque le programme a été lié. Rétablir les liens et spécifiez la bibliothèque C dernier.
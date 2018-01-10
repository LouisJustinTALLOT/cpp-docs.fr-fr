---
title: "Présentation de la fonction d’assistance | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, helper function
- __delayLoadHelper2 function
- delayimp.lib
- __delayLoadHelper function
- delayhlp.cpp
- delayimp.h
- helper functions
ms.assetid: 6279c12c-d908-4967-b0b3-cabfc3e91d3d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c3a013cf584c37f84331a5ab5dfe74eaa213c851
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-the-helper-function"></a>Présentation de la fonction d'assistance
La fonction d’assistance pour la prise en charge de l’éditeur de liens le chargement différé est ce qui charge réellement la DLL au moment de l’exécution. Vous pouvez modifier la fonction d’assistance pour personnaliser son comportement en écrivant votre propre fonction et en le liant à votre programme au lieu d’utiliser la fonction d’assistance fournie dans Delayimp.lib. Une fonction d’assistance sert toutes les DLL à chargement différé.  
  
 Vous pouvez fournir votre propre version de la fonction d’assistance si vous souhaitez effectuer un traitement spécifique selon les noms des DLL ou des importations.  
  
 La fonction d’assistance effectue les actions suivantes :  
  
-   Vérification du handle stocké dans la bibliothèque pour voir s’il a déjà été chargé.  
  
-   Appels **LoadLibrary** tentative de chargement de la DLL  
  
-   Appels **GetProcAddress** pour tenter d’obtenir l’adresse de la procédure  
  
-   Retourne à l’importation de délai charge la conversion de code pour appeler le point d’entrée chargé  
  
 La fonction d’assistance peut rappeler un raccordement de notification dans votre programme après chacune des actions suivantes :  
  
-   Au démarrage de la fonction d’assistance  
  
-   Juste avant **LoadLibrary** est appelée dans la fonction d’assistance  
  
-   Juste avant **GetProcAddress** est appelée dans la fonction d’assistance  
  
-   Si l’appel à **LoadLibrary** dans la fonction d’assistance a échoué  
  
-   Si l’appel à **GetProcAddress** dans la fonction d’assistance a échoué  
  
-   Après l’application d’assistance fonction s’effectue le traitement  
  
 Chacun de ces points de raccordement peut retourner une valeur qui modifie le traitement normal de la routine d’assistance de quelque façon, sauf le retour vers le thunk de chargement différé.  
  
 Le code de programme d’assistance par défaut peut être trouvé dans Delayhlp.cpp et Delayimp.h (dans vc\include) et est compilé dans Delayimp.lib (dans vc\lib). Vous devez inclure cette bibliothèque dans vos compilations, sauf si vous écrivez votre propre fonction d’assistance.  
  
 Les rubriques suivantes décrivent la fonction d’assistance :  
  
-   [Modifications apportées à la fonction d’assistance du chargement différé des DLL depuis Visual C++ 6.0](../../build/reference/changes-in-the-dll-delayed-loading-helper-function-since-visual-cpp-6-0.md)  
  
-   [Conventions d’appel, paramètres et type de retour](../../build/reference/calling-conventions-parameters-and-return-type.md)  
  
-   [Définitions des structures et constantes](../../build/reference/structure-and-constant-definitions.md)  
  
-   [Calcul des valeurs nécessaires](../../build/reference/calculating-necessary-values.md)  
  
-   [Déchargement d’une DLL à chargement différé](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)
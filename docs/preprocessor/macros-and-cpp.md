---
title: Macros et C++ | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7af092d31fb4495be47c88aaaf8830cc05db2bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="macros-and-c"></a>Macros et C++
C++ offre de nouvelles fonctionnalités, dont certaines supplantent celles proposés par le préprocesseur ANSI C. Ces nouvelles fonctionnalités améliorent la sécurité et la prévisibilité des types du langage :  
  
-   En C++, les objets déclarés comme **const** peut être utilisé dans les expressions constantes. Cela permet aux programmes de déclarer des constantes comportant des informations de type et de valeur, et des énumérations qui peuvent être affichées symboliquement avec le débogueur. Utiliser la directive `#define` du préprocesseur pour définir des constantes n'est pas aussi précis. Aucun stockage n’est alloué pour un **const** , sauf si une expression prenant son adresse est trouvée dans le programme de l’objet.  
  
-   La fonctionnalité de la fonction inline C++ supplante les macros de type fonction. Voici les avantages que présente l'utilisation des fonctions inline par rapport aux macros :  
  
    -   Sécurité de type. Les fonctions inline sont soumises à la même vérification du type que les fonctions normales. Les macros ne sont pas de type sécurisé.  
  
    -   Gestion correcte des arguments présentant des effets secondaires. Les fonctions inline évaluent les expressions fournies comme arguments avant l'accès au corps de la fonction. Par conséquent, il n'y a aucun risque qu'une expression avec effets secondaires présente un risque.  
  
 Pour plus d’informations sur les fonctions inline, consultez [inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md).  
  
 À des fins de compatibilité descendante, toutes les fonctions de préprocesseur qui existaient dans les spécifications C ANSI et C ++ antérieures sont conservés pour Microsoft C++.  
  
## <a name="see-also"></a>Voir aussi  
 [Macros prédéfinies](../preprocessor/predefined-macros.md)   
 [Macros (C/C++)](../preprocessor/macros-c-cpp.md)
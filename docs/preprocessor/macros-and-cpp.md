---
title: Macros et C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 746b04113e4cb49716e0c1fa6dee69a250bded42
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849611"
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
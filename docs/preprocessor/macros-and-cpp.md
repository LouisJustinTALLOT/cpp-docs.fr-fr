---
title: Macros et C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 8a86fb81544af91d4e844fb08b7948a589976e04
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220803"
---
# <a name="macros-and-c"></a>Macros et C++

C++offre de nouvelles fonctionnalités, dont certaines remplacent celles offertes par le préprocesseur ANSI C. Ces nouvelles fonctionnalités améliorent la sécurité et la prévisibilité des types du langage :

- Dans C++, les objets déclarés comme **const** peuvent être utilisés dans des expressions constantes. Elle permet aux programmes de déclarer des constantes qui contiennent des informations de type et de valeur. Ils peuvent déclarer des énumérations qui peuvent être affichées symboliquement avec le débogueur. Lorsque vous utilisez la `#define` directive de préprocesseur pour définir des constantes, elles ne sont pas aussi précises et non de type sécurisé. Aucun stockage n’est alloué pour un objet const, sauf si le programme contient une expression qui prend son adresse.

- La fonctionnalité de la fonction inline C++ supplante les macros de type fonction. Voici les avantages que présente l'utilisation des fonctions inline par rapport aux macros :

  - Sécurité de type. Les fonctions inline sont soumises à la même vérification du type que les fonctions normales. Les macros ne sont pas de type sécurisé.

  - Gestion correcte des arguments présentant des effets secondaires. Les fonctions inline évaluent les expressions fournies en tant qu’arguments avant que le corps de la fonction soit entré. Par conséquent, il n’y a aucun risque qu’une expression avec des effets secondaires ne soit pas sûre.

Pour plus d’informations sur les fonctions inline, consultez [inline, \_](../cpp/inline-functions-cpp.md)_ _ Inline, _forceinline.

À des fins de compatibilité descendante, toutes les fonctions de préprocesseur qui existaient dans les spécifications C ANSI et C ++ antérieures sont conservés pour Microsoft C++.

## <a name="see-also"></a>Voir aussi

[Macros prédéfinies](../preprocessor/predefined-macros.md)\
[Macros (C/C++)](../preprocessor/macros-c-cpp.md)

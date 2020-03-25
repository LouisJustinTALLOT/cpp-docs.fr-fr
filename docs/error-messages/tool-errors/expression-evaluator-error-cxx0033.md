---
title: Évaluateur d'expression, erreur CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 2916808d98f1fabc2157fbedc96d76e196661279
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195511"
---
# <a name="expression-evaluator-error-cxx0033"></a>Évaluateur d'expression, erreur CXX0033

erreur dans les informations de type OMF

Le fichier exécutable n’avait pas de format de module objet (OMF) valide pour le débogage.

Cette erreur est identique à CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le fichier exécutable n’a pas été créé avec l’éditeur de liens fourni avec cette version C++de Visual. Reliez le code de l’objet à l’aide de la version actuelle de LINK. exe.

1. Le fichier. exe a peut-être été endommagé. Recompilez et reliez le programme.

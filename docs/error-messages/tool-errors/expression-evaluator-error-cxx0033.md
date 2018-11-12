---
title: Évaluateur d'expression, erreur CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642783"
---
# <a name="expression-evaluator-error-cxx0033"></a>Évaluateur d'expression, erreur CXX0033

erreur dans les informations de type OMF

Le fichier exécutable n’avait pas un format de module d’objet valide (OMF) pour le débogage.

Cette erreur est identique à CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le fichier exécutable n’a pas été créé avec l’éditeur de liens fourni avec cette version de Visual C++. Relier le code de l’objet à l’aide de la version actuelle de LINK.exe.

1. Le fichier .exe est peut-être endommagé. Recompilez et rééditez le programme.
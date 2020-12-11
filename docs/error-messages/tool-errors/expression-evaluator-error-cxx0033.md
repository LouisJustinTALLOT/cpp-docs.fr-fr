---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0033'
title: Évaluateur d'expression, erreur CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 714499d8d1bc0812395576fe27be690997982065
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160322"
---
# <a name="expression-evaluator-error-cxx0033"></a>Évaluateur d'expression, erreur CXX0033

erreur dans les informations de type OMF

Le fichier exécutable n’avait pas de format de module objet (OMF) valide pour le débogage.

Cette erreur est identique à CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le fichier exécutable n’a pas été créé avec l’éditeur de liens fourni avec cette version de Visual C++. Reliez le code de l’objet à l’aide de la version actuelle de LINK.exe.

1. Le fichier. exe a peut-être été endommagé. Recompilez et reliez le programme.

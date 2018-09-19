---
title: Évaluateur d’expression, erreur CXX0033 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04f37b53c30d36a43d339132bfd9baca3e5ec70c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057195"
---
# <a name="expression-evaluator-error-cxx0033"></a>Évaluateur d'expression, erreur CXX0033

erreur dans les informations de type OMF

Le fichier exécutable n’avait pas un format de module d’objet valide (OMF) pour le débogage.

Cette erreur est identique à CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Le fichier exécutable n’a pas été créé avec l’éditeur de liens fourni avec cette version de Visual C++. Relier le code de l’objet à l’aide de la version actuelle de LINK.exe.

1. Le fichier .exe est peut-être endommagé. Recompilez et rééditez le programme.
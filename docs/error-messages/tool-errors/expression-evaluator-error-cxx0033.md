---
title: Évaluateur d’expression, erreur CXX0033 | Documents Microsoft
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
ms.openlocfilehash: 720b1aec6c9be16879119bc0e8148a301507577a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299498"
---
# <a name="expression-evaluator-error-cxx0033"></a>Évaluateur d'expression, erreur CXX0033
erreur dans les informations de type OMF  
  
 Le fichier exécutable n’avait pas un format de module valide d’objet (OMF) pour le débogage.  
  
 Cette erreur est identique à CAN0033.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Le fichier exécutable n’a pas été créé avec l’éditeur de liens fourni avec cette version de Visual C++. Reconstruire le code de l’objet à l’aide de la version actuelle de LINK.exe.  
  
2.  Le fichier .exe a peut-être été endommagé. Recompilez et rééditez le programme.
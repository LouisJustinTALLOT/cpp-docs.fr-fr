---
title: Exit (fonction) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
ms.assetid: 26ce439f-81e2-431c-9ff8-a09a96f32127
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5767f6b08b4adcd3d1a8d367c6286a746eeecec3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412528"
---
# <a name="exit-function"></a>exit, fonction
Le **quitter** fonction, déclarée dans le fichier include standard \<stdlib.h >, met fin à un programme C++.  
  
 La valeur fournie comme argument à **quitter** est retournée au système d’exploitation en tant que code retour de code ou de sortie du programme. Par convention, un code de retour égal à zéro signifie que le programme s'est terminé correctement.  
  
> [!NOTE]
>  Vous pouvez utiliser l’une des constantes `EXIT_FAILURE` et `EXIT_SUCCESS`, défini dans \<stdlib.h >, pour indiquer la réussite ou l’échec de votre programme.  
  
 Émettre un `return` instruction à partir de la **principal** fonction équivaut à appeler le **quitter** fonction avec la valeur de retour comme argument.  
  
 Pour plus d’informations, consultez [quitter](../c-runtime-library/reference/exit-exit-exit.md) dans les *Run-Time Library Reference*.  
  
## <a name="see-also"></a>Voir aussi  
 [Terminaison du programme](../cpp/program-termination.md)
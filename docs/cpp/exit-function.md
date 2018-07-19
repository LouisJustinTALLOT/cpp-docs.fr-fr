---
title: Fonction Exit | Microsoft Docs
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
ms.openlocfilehash: d08ac1375fa383543eaafb5b3ce49cd2bbfbc4da
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941078"
---
# <a name="exit-function"></a>exit, fonction
Le `exit` fonction, déclarée dans le fichier include standard \<stdlib.h >, met fin à un programme C++.  
  
 La valeur fournie en tant qu’argument à `exit` est retourné au système d’exploitation en tant que code retour de code ou de sortie du programme. Par convention, un code de retour égal à zéro signifie que le programme s'est terminé correctement.  
  
> [!NOTE]
>  Vous pouvez utiliser les constantes EXIT_FAILURE et EXIT_SUCCESS, défini dans \<stdlib.h >, pour indiquer la réussite ou l’échec de votre programme.  
  
 Émission d’un **retourner** instruction à partir de la `main` fonction équivaut à appeler le `exit` fonction avec la valeur de retour comme argument.  
  
 Pour plus d’informations, consultez [quitter](../c-runtime-library/reference/exit-exit-exit.md) dans le *Run-Time Library Reference*.  
  
## <a name="see-also"></a>Voir aussi  
 [Terminaison du programme](../cpp/program-termination.md)
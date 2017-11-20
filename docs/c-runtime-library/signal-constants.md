---
title: Constantes signal | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs: C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fddb279acfbb6d8841ac17a27cd43de205dc9dbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="signal-constants"></a>signal, constantes
## <a name="syntax"></a>Syntaxe  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>Remarques  
 L’argument `sig` doit être une des constantes manifestes répertoriées ci-dessous (définies dans SIGNAL.H).  
  
 `SIGABRT`  
 Arrêt anormal. L’action par défaut termine le programme appelant avec le code de sortie 3.  
  
 `SIGABRT_COMPAT`  
 Identique à SIGABRT. Pour la compatibilité avec les autres plateformes.  
  
 `SIGFPE`  
 Erreur de virgule flottante, comme le dépassement de capacité, la division par zéro ou une opération non valide. L’action par défaut termine le programme appelant.  
  
 `SIGILL`  
 Instruction non conforme. L’action par défaut termine le programme appelant.  
  
 `SIGINT`  
 Interruption CTRL+C. L’action par défaut termine le programme appelant avec le code de sortie 3.  
  
 `SIGSEGV`  
 Accès au stockage non conforme. L’action par défaut termine le programme appelant.  
  
 `SIGTERM`  
 Demande d’arrêt envoyée au programme. L’action par défaut termine le programme appelant avec le code de sortie 3.  
  
 `SIG_ERR`  
 Un type de retour d’un signal indiquant une erreur s’est produite.  
  
## <a name="see-also"></a>Voir aussi  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)
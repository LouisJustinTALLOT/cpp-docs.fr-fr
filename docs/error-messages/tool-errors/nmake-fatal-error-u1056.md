---
title: Erreur irrécupérable NMAKE U1056 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1056
dev_langs:
- C++
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19890e290c98fd9602d755ad35f9d47204bd6c24
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316554"
---
# <a name="nmake-fatal-error-u1056"></a>Erreur irrécupérable NMAKE U1056
Impossible de trouver le processeur de commandes  
  
 Le processeur de commandes n’était pas dans le chemin d’accès spécifié dans le **COMSPEC** ou **chemin d’accès** variables d’environnement.  
  
 NMAKE utilise COMMAND.COM ou CMD. EXE en tant qu’un interpréteur de commandes lors de l’exécution de commandes. Il recherche l’interpréteur de commandes d’abord dans le chemin d’accès défini dans **COMSPEC**. Si **COMSPEC** n’existe pas, les répertoires spécifiés dans des recherches NMAKE **chemin d’accès**.
---
title: Erreur irrécupérable NMAKE U1064 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1064
dev_langs:
- C++
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5573943fc2c274d48768933a634b2c052361a8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332138"
---
# <a name="nmake-fatal-error-u1064"></a>Erreur irrécupérable NMAKE U1064
MAKEFILE non trouvé et aucune cible spécifiée  
  
 La ligne de commande NMAKE n’a pas spécifié un makefile ou une cible, et le répertoire en cours ne contenait pas un fichier nommé MAKEFILE.  
  
 NMAKE exige un makefile ou une cible de ligne de commande (ou les deux). Pour mettre un makefile à la disposition de NMAKE, spécifiez l’option /F ou placez un fichier nommé MAKEFILE dans le répertoire actif. NMAKE peut créer une cible de ligne de commande à l’aide d’une règle d’inférence si un makefile n’est pas fourni.
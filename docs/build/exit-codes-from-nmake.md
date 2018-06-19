---
title: Codes de sortie de NMAKE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e71442e1e36dbd69afa65051cbf08f403bf8b31
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367093"
---
# <a name="exit-codes-from-nmake"></a>Codes de sortie de NMAKE
NMAKE retourne les codes de sortie suivants :  
  
|Code|Signification|  
|----------|-------------|  
|0|Aucune erreur (probablement un avertissement)|  
|1|Génération incomplète (émise seulement quand l’option /K est utilisée)|  
|2|Erreur de programme, probablement en raison d’une des valeurs suivantes :|  
||-Une erreur de syntaxe dans le makefile|  
||-Un erreur ou code de sortie à partir d’une commande|  
||-Une interruption par l’utilisateur|  
|4|Erreur système : mémoire insuffisante|  
|255|Cible n’est pas à jour (émis seulement quand l’option /Q est utilisée)|  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de NMAKE](../build/running-nmake.md)
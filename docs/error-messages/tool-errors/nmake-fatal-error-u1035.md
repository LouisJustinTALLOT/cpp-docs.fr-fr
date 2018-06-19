---
title: Erreur irrécupérable NMAKE U1035 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb32f815345b933ad6a65a0c8c1ec8ad59cbe81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322794"
---
# <a name="nmake-fatal-error-u1035"></a>Erreur irrécupérable NMAKE U1035
Erreur de syntaxe : attendu ' :' ou '=' un séparateur  
  
 Signe deux-points (**:**) ou un signe égal (**=**) était attendu.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Un signe deux-points n’est pas suivie d’une cible.  
  
2.  Un signe deux-points et aucun espace (par exemple, a:) suivi une cible de lettre unique. NMAKE interprète cela comme une spécification de lecteur.  
  
3.  Un signe deux-points n’est pas suivie d’une règle d’inférence.  
  
4.  Une définition de macro n’est pas suivie par un signe égal.  
  
5.  Un caractère suivi d’une barre oblique inverse (**\\**) qui a été utilisé pour une commande continue sur une nouvelle ligne.  
  
6.  Une chaîne qui n’est pas suivie par une règle de syntaxe NMAKE a été trouvé.  
  
7.  Le makefile a été mis en forme par un traitement de texte.
---
title: Erreur irrécupérable C1055 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07f0dc0e8dca08e8b0de47b73516d3fdfa21435b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225340"
---
# <a name="fatal-error-c1055"></a>Erreur irrécupérable C1055
limite du compilateur : clés insuffisantes  
  
 Le fichier source contient trop de symboles. Le compilateur a manqué de clés de hachage pour la table de symboles.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.  
  
1.  Fractionnez le fichier source en fichiers plus petits.  
  
2.  Éliminez les fichiers d’en-tête.  
  
3.  Réutiliser des variables temporaires et globales au lieu de créer de nouveaux.
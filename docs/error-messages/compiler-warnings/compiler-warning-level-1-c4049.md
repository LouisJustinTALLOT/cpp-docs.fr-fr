---
title: Compilateur avertissement (niveau 1) C4049 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1eea293ff64ed8fe2bf4bf0d38d897eb82223802
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276827"
---
# <a name="compiler-warning-level-1-c4049"></a>Compilateur avertissement (niveau 1) C4049
limite du compilateur : arrêt de l’émission de numéros de ligne  
  
 Le fichier contient plus de 16 777 215 (2<sup>24</sup>-1) lignes sources. Le compilateur arrête la numérotation à 16 777 215.  
  
 Pour le code après la ligne 16 777 215 :  
  
-   L’image ne contient aucune information de débogage pour les numéros de ligne.  
  
-   Certains diagnostics peuvent être signalés avec des numéros de ligne.  
  
-   listes .asm (/ FA) peut avoir des numéros de ligne.
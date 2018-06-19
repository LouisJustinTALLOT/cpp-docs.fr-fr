---
title: Erreur irrécupérable C1013 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1013
dev_langs:
- C++
helpviewer_keywords:
- C1013
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00b5dae643ec20e9d7d8a8dcdf41d9debe7e6b7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198636"
---
# <a name="fatal-error-c1013"></a>Erreur irrécupérable C1013
limite du compilateur : parenthèses ouvertes trop nombreuses  
  
 Une expression contient trop de niveaux de parenthèses pour une même expression. Simplifiez l’expression ou scindez-la en plusieurs instructions.  
  
 Avant Visual C++ 6.0 Service Pack 3, la limite d’imbrication de parenthèses dans une même expression était de 59. Actuellement, cette limite est de 256.
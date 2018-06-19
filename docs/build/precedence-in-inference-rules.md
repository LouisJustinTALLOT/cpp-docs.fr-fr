---
title: Priorité dans les règles d’inférence | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- precedence, inference rule
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36d462d4222cbfc143dd7487d4cb6b1b8bb3ba3b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368484"
---
# <a name="precedence-in-inference-rules"></a>Priorité dans les règles d'inférence
Si une règle d’inférence est définie plusieurs fois, NMAKE utilise la définition de la priorité la plus élevée. La liste suivante indique l’ordre de priorité, du plus élevé au plus bas :  
  
1.  Une règle d’inférence définie dans un makefile ; définitions les plus récentes ont une priorité.  
  
2.  Une règle d’inférence définie dans Tools.ini ; définitions les plus récentes ont une priorité.  
  
3.  Règle d’inférence prédéfinie.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’inférence](../build/inference-rules.md)
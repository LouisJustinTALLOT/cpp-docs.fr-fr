---
title: Évaluateur d’expression, erreur CXX0069 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0069
dev_langs:
- C++
helpviewer_keywords:
- CXX0069
ms.assetid: cf334b23-1e17-4d37-acc5-18597ee84164
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14cf468ebd2d8d40f306a2fa80a0331d7667d0d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299664"
---
# <a name="expression-evaluator-error-cxx0069"></a>Évaluateur d'expression, erreur CXX0069
variable a besoin du frame de pile  
  
 L’évaluateur d’expression ne peut pas évaluer la variable, car il ne figure pas dans un frame de pile. Cela peut être dû aux variables déclarées dans le cadre d’une fonction inline.
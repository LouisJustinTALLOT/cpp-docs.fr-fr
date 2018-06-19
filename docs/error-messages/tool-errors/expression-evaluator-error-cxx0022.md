---
title: Évaluateur d’expression, erreur CXX0022 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0022
dev_langs:
- C++
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 822e07c9173d9010bb8ab63b6ca4837b9c52e066
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33297652"
---
# <a name="expression-evaluator-error-cxx0022"></a>Évaluateur d'expression, erreur CXX0022
appel de fonction avant _main  
  
 L’évaluateur d’expression C ne peut pas évaluer une fonction avant que le débogueur est passé à la fonction **_main**. Le programme n’est pas initialisé correctement tant que **_main** a été appelée.  
  
 Cette erreur est identique à CAN0022.
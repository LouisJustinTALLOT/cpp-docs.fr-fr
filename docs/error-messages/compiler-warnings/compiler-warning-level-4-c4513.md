---
title: Compilateur avertissement (niveau 4) C4513 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4513
dev_langs:
- C++
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92c3e89204ec30f9c96a5ea03ede5093dd013d0c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292894"
---
# <a name="compiler-warning-level-4-c4513"></a>Avertissement du compilateur (niveau 4) C4513
'classe' : destructeur n’a pas pu être généré.  
  
 Le compilateur ne peut pas générer un destructeur par défaut pour la classe donnée ; aucun destructeur n’a été créé. Le destructeur est dans une classe de base qui n’est pas accessible à la classe dérivée. Si la classe de base a un destructeur privé, déclarez-le public ou protégé.
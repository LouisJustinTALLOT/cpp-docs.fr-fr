---
title: Erreur du compilateur C2170 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2170
dev_langs:
- C++
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad0d19dff10d04d155d8071ffb349664f6b3104e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171088"
---
# <a name="compiler-error-c2170"></a>Erreur du compilateur C2170
'identificateur' : non déclaré comme fonction, ne peut pas être intrinsèque  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Pragma `intrinsic` est utilisé pour un élément autre qu’une fonction.  
  
2.  Pragma `intrinsic` est utilisé pour une fonction sans forme intrinsèque.
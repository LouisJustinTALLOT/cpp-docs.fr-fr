---
title: Erreur du compilateur C2097 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa4b867c7f043d796f208fdc7100509893147daf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33168358"
---
# <a name="compiler-error-c2097"></a>Erreur du compilateur C2097
initialisation non conforme  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Initialisation d’une variable à l’aide d’une valeur non constante.  
  
2.  Initialisation d’une adresse courte avec une adresse longue.  
  
3.  L’initialisation d’une structure locale, une union ou un tableau avec une expression non constante lors de la compilation avec **/Za**.  
  
4.  Initialisation avec une expression contenant un opérateur virgule.  
  
5.  Initialisation avec une expression ni constante ni symbolique.
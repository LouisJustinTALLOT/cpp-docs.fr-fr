---
title: Compilateur avertissement (niveau 3) C4306 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4306
dev_langs:
- C++
helpviewer_keywords:
- C4306
ms.assetid: 5b2192d7-402d-4b6d-8619-08105e7dcac7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99a490fc90ee9a977442548406ea2aec4baac3fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299001"
---
# <a name="compiler-warning-level-3-c4306"></a>Avertissement du compilateur (niveau 3) C4306
**'**   
 ***identificateur* ' : conversion de '**   
 ***type1* 'à'**   
 ***type2* ' d’une taille supérieure**  
  
 L’identificateur est le type converti en un pointeur de plus grand. Les bits de poids fort non remplis du nouveau type seront remplies de zéros.  
  
 Cet avertissement peut indiquer une conversion non désirée. Le pointeur résultant n’est peut-être pas valid.
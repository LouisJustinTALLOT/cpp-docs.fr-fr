---
title: Compilateur avertissement (niveau 1) C4612 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4612
dev_langs:
- C++
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0983f5d0bb89eaf1daee94468b318557bc83cd05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281880"
---
# <a name="compiler-warning-level-1-c4612"></a>Avertissement du compilateur (niveau 1) C4612
erreur dans le nom de fichier Include  
  
 Cet avertissement se produit avec **#pragma include_alias** quand un nom de fichier est incorrect ou manquant.  
  
 Les arguments de la **#pragma include_alias** instruction permettre utiliser les guillemets de (**»***nom de fichier***»**) ou les crochets pointus ( **\< ***nom de fichier***>**), mais les deux doivent utiliser le même formulaire.  
  
## <a name="example"></a>Exemple  
  
```  
// C4612.cpp  
// compile with: /W1 /LD  
#pragma include_alias("StandardIO", <stdio.h>) // C4612  
```
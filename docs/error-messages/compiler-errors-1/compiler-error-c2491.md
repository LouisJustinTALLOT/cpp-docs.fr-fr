---
title: Erreur du compilateur C2491 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2491
dev_langs:
- C++
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1e46d63f6602af7fe962f8b139c93a4b9a561783
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198883"
---
# <a name="compiler-error-c2491"></a>Erreur du compilateur C2491
'identificateur' : définition de la fonction dllimport non autorisée  
  
 Données, données membres static et fonctions peuvent être déclarées comme `dllimport` mais pas définies comme `dllimport`.  
  
 Pour résoudre ce problème, supprimez le spécificateur `__declspec(dllimport)` de la définition de la fonction.  
  
 L'exemple suivant génère l'erreur C2491 :  
  
```  
// C2491.cpp  
// compile with: /c  
// function definition  
void __declspec(dllimport) funcB() {}   // C2491  
  
// function declaration  
void __declspec(dllimport) funcB();   // OK  
```
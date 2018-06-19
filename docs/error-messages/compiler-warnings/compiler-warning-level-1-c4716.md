---
title: Compilateur avertissement (niveau 1) C4716 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4716
dev_langs:
- C++
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be620264c315fc9c2ff3cd4cb91bd9d77c8a4d07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288851"
---
# <a name="compiler-warning-level-1-c4716"></a>Avertissement du compilateur (niveau 1) C4716
'fonction' doit retourner une valeur  
  
 La fonction donnée n’a pas retourné une valeur.  
  
 Fonctionne uniquement avec un type de retour void peuvent utiliser la commande return sans valeur de retour associée.  
  
 Une valeur non définie s’affichera lorsque cette fonction est appelée.  
  
 Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md).  
  
 L’exemple suivant génère C4716 :  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```
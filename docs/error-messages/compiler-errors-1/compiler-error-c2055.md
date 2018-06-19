---
title: Erreur du compilateur C2055 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2055
dev_langs:
- C++
helpviewer_keywords:
- C2055
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f16d9c3948c0211da69142f1b9c7c1a6a32d8c37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169330"
---
# <a name="compiler-error-c2055"></a>Erreur du compilateur C2055
liste de paramètres formels attendue, non une liste de type  
  
 Une définition de fonction contient une liste de type de paramètre au lieu d’une liste de paramètres formels. C ANSI requiert des paramètres formels à être appelé à moins d’être void ou des points de suspension (`...`).  
  
 L’exemple suivant génère l’erreur C2055 :  
  
```  
// C2055.c  
// compile with: /c  
void func(int, char) {}  // C2055  
void func (int i, char c) {}   // OK  
```
---
title: Erreur du compilateur C3140 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3140
dev_langs:
- C++
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2c8c9e47020fe53e87b985b5db6192cd26098fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246902"
---
# <a name="compiler-error-c3140"></a>Erreur du compilateur C3140
ne peut pas avoir plusieurs attributs 'module' dans la même unité de compilation  
  
 Le [module](../../windows/module-cpp.md) attribut peut uniquement être défini qu’une seule fois par projet.  
  
 L’exemple suivant génère l’erreur C3140 :  
  
```  
// C3140.cpp  
// compile with: /c  
[emitidl];  
[module(name = "MyLibrary")];  
[module(name = "MyLibrary2")];   // C3140  
```
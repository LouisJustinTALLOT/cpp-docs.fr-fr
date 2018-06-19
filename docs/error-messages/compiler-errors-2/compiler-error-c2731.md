---
title: Erreur du compilateur C2731 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2731
dev_langs:
- C++
helpviewer_keywords:
- C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f925a781501b2dfd3ed2297319d49cc27854a78a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231899"
---
# <a name="compiler-error-c2731"></a>Erreur du compilateur C2731
'identificateur' : fonction ne peut pas être surchargée.  
  
 Les fonctions `main`, `WinMain`, `DllMain`, et `LibMain` ne peut pas être surchargé.  
  
 L’exemple suivant génère l’erreur C2731 :  
  
```  
// C2731.cpp  
extern "C" void WinMain(int, char *, char *);  
void WinMain(int, short, char *, char*);   // C2731  
```
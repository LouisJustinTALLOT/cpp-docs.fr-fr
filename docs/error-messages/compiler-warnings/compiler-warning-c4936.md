---
title: Avertissement du compilateur C4936 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcf9f32a4a1b1e43cb4bd69c754e3ae3a98bff3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4936"></a>Avertissement du compilateur C4936
ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure  
  
 Le **/CLR : pure** option du compilateur est déconseillée dans Visual Studio 2015.  
  
 Un modificateur `__declspec` a été utilisé, mais ce modificateur `__declspec` est valide uniquement quand il est compilé avec l’une des options [/clr](../../build/reference/clr-common-language-runtime-compilation.md) .  
  
 Pour plus d’informations, consultez [appdomain](../../cpp/appdomain.md) et [process](../../cpp/process.md).  
  
 C4936 est toujours émis en tant qu’erreur.  Vous pouvez désactiver C4936 avec le pragma [warning](../../preprocessor/warning.md) .  
  
 L’exemple suivant génère l’avertissement C4936 :  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```
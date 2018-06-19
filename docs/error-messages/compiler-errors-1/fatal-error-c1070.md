---
title: Erreur irrécupérable C1070 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1070
dev_langs:
- C++
helpviewer_keywords:
- C1070
ms.assetid: 1058269a-5db6-4c23-a97f-b5269eb9188b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 99650b93819c4bc0192d612b0f1344e1b99671d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228173"
---
# <a name="fatal-error-c1070"></a>Erreur irrécupérable C1070
non concordance #if/#endif dans le fichier 'nom_fichier'  
  
 Une directive `#if`, `#ifdef`ou `#ifndef` n’a pas de `#endif`correspondant.  
  
 L’exemple suivant génère l’erreur C1070 :  
  
```  
// C1070.cpp  
#define TEST  
  
#ifdef TEST  
  
#ifdef TEST  
#endif  
// C1070  
```  
  
 Solution possible :  
  
```  
// C1070b.cpp  
// compile with: /c  
#define TEST  
  
#ifdef TEST  
#endif  
  
#ifdef TEST  
#endif  
```
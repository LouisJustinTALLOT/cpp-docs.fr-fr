---
title: Erreur du compilateur C2755 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2755
dev_langs:
- C++
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a018554de91003b54ffc403f1527ca07f2d4a75
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233526"
---
# <a name="compiler-error-c2755"></a>Erreur du compilateur C2755
'param' : un paramètre sans type d’une spécialisation partielle doit être un identificateur simple  
  
 Le paramètre sans type doit être un identificateur simple, quelque chose que le compilateur peut résoudre au moment de la compilation à un identificateur unique ou une valeur constante.  
  
 L’exemple suivant génère l’erreur C2755 :  
  
```  
// C2755.cpp  
template<int I, int J>  
struct A {};  
  
template<int I>   
struct A<I,I*5> {};   // C2755  
// try the following line instead  
// struct A<I,5> {};  
```
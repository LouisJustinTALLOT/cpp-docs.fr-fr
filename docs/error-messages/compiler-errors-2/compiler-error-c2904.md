---
title: Erreur du compilateur C2904 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2904
dev_langs:
- C++
helpviewer_keywords:
- C2904
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 003f907cd82abb5d3aa2ce8502074cc39d16699b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245813"
---
# <a name="compiler-error-c2904"></a>Erreur du compilateur C2904
'identificateur' : nom déjà utilisé pour un modèle dans la portée actuelle  
  
 Vérifiez si le code contient des noms dupliqués.  
  
 L’exemple suivant génère l’erreur C2904 :  
  
```  
// C2904.cpp  
// compile with: /c  
void X();  // X is declared as a function  
template<class T> class X{};  // C2904  
```
---
title: Erreur du compilateur C2803 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2803
dev_langs:
- C++
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51cf2a8b38a86fcd97ab693b3853fe25527a0bb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236221"
---
# <a name="compiler-error-c2803"></a>Erreur du compilateur C2803
'operator opérateur' doit avoir au moins un paramètre de type classe  
  
 L’opérateur surchargé ne dispose pas d’un paramètre de type de classe.  
  
 Vous devez passer au moins un paramètre par référence (ne pas à l’aide de pointeurs, mais des références) ou par valeur pour pouvoir écrire » une < b » (un de la classe de type A et b).  
  
 Si les deux paramètres sont des pointeurs sera une pure comparaison d’adresses de pointeur et n’utilise pas la conversion définie par l’utilisateur.  
  
 L’exemple suivant génère l’erreur C2803 :  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```
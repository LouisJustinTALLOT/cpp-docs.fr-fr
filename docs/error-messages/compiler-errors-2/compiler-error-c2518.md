---
title: Erreur du compilateur C2518 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2518
dev_langs:
- C++
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2a76c528def49b1235460fa4d6632efd196417d3
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2518"></a>Erreur du compilateur C2518
mot clé 'mot_clé' non conforme dans une liste de classes de base ; ignoré  
  
 Les mots clés `class` et `struct` ne doivent pas apparaître dans une liste de classes de base.  
  
 L’exemple suivant génère l’erreur C2518 :  
  
```  
// C2518.cpp  
// compile with: /c  
class B {};  
class C : public class B {};   // C2518  
class D: public B {};   // OK  
```

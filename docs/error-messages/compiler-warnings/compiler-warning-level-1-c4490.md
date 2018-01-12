---
title: Compilateur avertissement (niveau 1) C4490 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4490
dev_langs: C++
helpviewer_keywords: C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05ca17f42cee490073a5a2bab8793ac520be45c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4490"></a>Avertissement du compilateur (niveau 1) C4490
'override' : utilisation incorrecte du spécificateur de substitution ; 'fonction' ne correspond pas à une méthode de classe ref de base  
  
 Un spécificateur de substitution a été utilisé incorrectement. Par exemple, vous ne substituez pas une fonction d’interface, vous l’implémenter.  
  
 Pour plus d’informations, consultez [des spécificateurs de substitution](../../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4490 :.  
  
```  
// C4490.cpp  
// compile with: /clr /c /W1  
  
interface struct IFace {  
   void Test();  
};  
  
ref struct Class1 : public IFace {  
   virtual void Test() override {}   // C4490  
   // try the following line instead  
   // virtual void Test() {}  
};  
```
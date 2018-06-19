---
title: Compilateur avertissement (niveau 1) C4621 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4621
dev_langs:
- C++
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: efefe6feacd79833e3ec51cc1f2274c142b2426a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281948"
---
# <a name="compiler-warning-level-1-c4621"></a>Avertissement du compilateur (niveau 1) C4621
aucune forme suffixée de l’opérateur 'operator--' trouvée pour le type 'type', utilisez la forme préfixée  
  
 Il n’a aucun opérateur de décrémentation suffixé défini pour le type donné. Le compilateur a utilisé l’opérateur de préfixe surchargé.  
  
 Cet avertissement peut être évité en définissant un suffixe `--` opérateur. Créer une version à deux arguments de la `--` opérateur, comme indiqué ci-dessous :  
  
```  
// C4621.cpp  
// compile with: /W1  
class A  
{  
public:  
   A(int nData) : m_nData(nData)  
   {  
   }  
  
   A operator--()  
   {  
      m_nData -= 1;  
      return *this;  
   }  
  
   // A operator--(int)  
   // {  
   //    A tmp = *this;  
   //    m_nData -= 1;  
   //    return tmp;  
   // }  
  
private:  
   int m_nData;  
};  
  
int main()  
{  
   A a(10);  
   --a;  
   a--;   // C4621  
}  
```
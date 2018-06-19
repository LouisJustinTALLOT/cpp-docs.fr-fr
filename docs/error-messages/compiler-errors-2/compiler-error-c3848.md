---
title: Erreur du compilateur C3848 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3848
dev_langs:
- C++
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37354d30ab20820657fc048cac0f87aa1a958dfa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267171"
---
# <a name="compiler-error-c3848"></a>Erreur du compilateur C3848
expression ayant le type 'type' perdrait certains qualificateurs const-volatile afin d’appeler 'fonction'  
  
 Une variable avec un type const-volatile peut uniquement appeler des membres fonctions avec des qualifications const-volatile égales ou supérieures.  
  
 Les exemples suivants génèrent C3848 :  
  
```  
// C3848.cpp  
void glbFunc1()  
{  
}  
  
typedef void (* pFunc1)();  
  
struct S3  
{  
   operator pFunc1() // const  
   {  
      return &glbFunc1;  
   }  
};  
  
int main()  
{  
   const S3 s3;  
   s3();   // C3848, uncomment const qualifier  
}  
```
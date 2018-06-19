---
title: Erreur du compilateur C3101 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3101
dev_langs:
- C++
helpviewer_keywords:
- C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8e10d3b22e7120789b9e1b6bb48fca097fcfddb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247454"
---
# <a name="compiler-error-c3101"></a>Erreur du compilateur C3101
expression non conforme pour un attribut nommé argument 'field'  
  
 Lors de l’initialisation d’un argument d’attribut nommé, la valeur doit être une constante de compilation.  
  
 Pour plus d’informations sur les attributs, consultez [les attributs définis par l’utilisateur](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3101.  
  
```  
// C3101.cpp  
// compile with: /clr /c  
ref class AAttribute : System::Attribute {  
public:  
   int Field;  
};  
  
extern int i;  
  
[assembly:A(Field = i)];   // C3101  
[assembly:A(Field = 0)];   // OK  
```
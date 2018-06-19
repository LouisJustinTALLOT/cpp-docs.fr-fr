---
title: Erreur du compilateur C3114 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3114
dev_langs:
- C++
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69001d415167f976d0f30c2dd5a0181cc032d0d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246266"
---
# <a name="compiler-error-c3114"></a>Erreur du compilateur C3114
'argument' : argument d’attribut nommé non valide  
  
 Dans l’ordre pour un membre de données de classe attribut soit un argument nommé valide, elle ne doit pas être marquée `static`, `const`, ou `literal`. Si une propriété, la propriété ne doit pas être `static` et doit avoir get et définir des accesseurs.  
  
 Pour plus d’informations, consultez [propriété](../../windows/property-cpp-component-extensions.md) et [les attributs définis par l’utilisateur](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3114.  
  
```  
// C3114.cpp  
// compile with: /clr /c  
public ref class A : System::Attribute {  
public:  
   static property int StaticProp {  
      int get();  
   }  
  
   property int Prop2 {  
      int get();  
      void set(int i);  
   }  
};  
  
[A(StaticProp=123)]   // C3114  
public ref class R {};  
  
[A(Prop2=123)]   // OK  
public ref class S {};  
```
---
title: Opérateurs définis par l’utilisateur (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7cf5583b3ae896ea252d191fbeba86e202b56cef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33174148"
---
# <a name="user-defined-operators-ccli"></a>Opérateurs définis par l'utilisateur (C++/CLI)
Les opérateurs définis par l’utilisateur pour les types managés sont autorisés en tant que membres statiques ou des membres d’instance, ou dans une portée globale. Toutefois, seuls les opérateurs statiques sont accessibles via les métadonnées pour les clients qui sont écrites dans une langue autre que Visual C++.  
  
 Dans un type référence, l’un des paramètres d’un opérateur défini par l’utilisateur statique doit être une de ces :  
  
-   Un handle (`type` ^) à une instance du type englobant.  
  
-   Une indirection de type référence (`type`^ & ou type ^ %) à un handle à une instance du type englobant.  
  
 Dans un type valeur, l’un des paramètres d’un opérateur défini par l’utilisateur statique doit être une de ces :  
  
-   De même type que le type englobant de valeur.  
  
-   Une indirection de type pointeur (`type`^) pour le type englobant.  
  
-   Une indirection de type référence (`type`% ou `type`&) pour le type englobant.  
  
-   Une indirection de type référence (`type`^ % ou `type`^ &) au handle.  
  
 Vous pouvez définir les opérateurs suivants :  
  
|Opérateur|Unaire/binaire Forms ?|  
|--------------|--------------------------|  
|!|Unaire|  
|!=|Binaire|  
|%|Binaire|  
|&|Unaire et binaire|  
|&&|Binaire|  
|*|Unaire et binaire|  
|+|Unaire et binaire|  
|++|Unaire|  
|,|Binaire|  
|-|Unaire et binaire|  
|--|Unaire|  
|->|Unaire|  
|/|Binaire|  
|<|Binaire|  
|<<|Binaire|  
|\<=|Binaire|  
|=|Binaire|  
|==|Binaire|  
|>|Binaire|  
|>=|Binaire|  
|>>|Binaire|  
|^|Binaire|  
|False|Unaire|  
|true|Unaire|  
|&#124;|Binaire|  
|&#124;&#124;|Binaire|  
|~|Unaire|  
  
## <a name="example"></a>Exemple  
  
```cpp  
// mcppv2_user-defined_operators.cpp  
// compile with: /clr  
using namespace System;  
public ref struct X {  
   X(int i) : m_i(i) {}  
   X() {}  
  
   int m_i;  
  
   // static, binary, user-defined operator  
   static X ^ operator + (X^ me, int i) {  
      return (gcnew X(me -> m_i + i));  
   }  
  
   // instance, binary, user-defined operator  
   X^ operator -( int i ) {  
      return gcnew X(this->m_i - i);  
   }  
  
   // instance, unary, user-defined pre-increment operator  
   X^ operator ++() {  
      return gcnew X(this->m_i++);  
   }  
  
   // instance, unary, user-defined post-increment operator  
   X^ operator ++(int i) {  
      return gcnew X(this->m_i++);  
   }  
  
   // static, unary user-defined pre- and post-increment operator  
   static X^ operator-- (X^ me) {  
      return (gcnew X(me -> m_i - 1));  
   }  
};  
  
int main() {  
   X ^hX = gcnew X(-5);  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX + 1;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX - (-1);  
   System::Console::WriteLine(hX -> m_i);  
  
   ++hX;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX++;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX--;  
   System::Console::WriteLine(hX -> m_i);  
  
   --hX;  
   System::Console::WriteLine(hX -> m_i);  
}  
```  
  
```Output  
-5  
-4  
-3  
-2  
-1  
-2  
-3  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre la synthèse d’opérateur, qui est disponible uniquement lorsque vous utilisez **/CLR** à compiler. Synthèse d’opérateur crée le formulaire de l’attribution d’un opérateur binaire, s’il n’est défini, où le côté gauche de l’opérateur d’assignation a un type CLR.  
  
```cpp  
// mcppv2_user-defined_operators_2.cpp  
// compile with: /clr  
ref struct A {  
   A(int n) : m_n(n) {};  
   static A^ operator + (A^ r1, A^ r2) {  
      return gcnew A( r1->m_n + r2->m_n);  
   };  
   int m_n;  
};  
  
int main() {  
   A^ a1 = gcnew A(10);  
   A^ a2 = gcnew A(20);  
  
   a1 += a2;   // a1 = a1 + a2   += not defined in source  
   System::Console::WriteLine(a1->m_n);  
}  
```  
  
```Output  
30  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)
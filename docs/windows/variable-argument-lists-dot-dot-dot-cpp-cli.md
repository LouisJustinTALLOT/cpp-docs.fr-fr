---
title: Listes d’arguments variables (...) (C + C++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eec0e3591da2417137fda3bae4ed9e7860472fb2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889821"
---
# <a name="variable-argument-lists--ccli"></a>Listes d’arguments de variable (...) (C++/CLI)
Cet exemple montre comment vous pouvez utiliser la `...` syntaxe dans Visual C++ pour implémenter des fonctions qui ont un nombre variable d’arguments.  
  
> [!NOTE]
>  Cette rubrique se rapporte à C + c++ / CLI. Pour plus d’informations sur l’utilisation de la `...` dans la norme ISO C++ Standard, consultez [Ellipses et modèles Variadiques](../cpp/ellipses-and-variadic-templates.md) et Ellipses et Arguments par défaut dans [expressions suffixées](../cpp/postfix-expressions.md).  
  
 Le paramètre utilise `...` doit être le dernier paramètre dans la liste de paramètres.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  
  
```  
// mcppv2_paramarray.cpp  
// compile with: /clr  
using namespace System;  
double average( ... array<Int32>^ arr ) {  
   int i = arr->GetLength(0);  
   double answer = 0.0;  
  
   for (int j = 0 ; j < i ; j++)  
      answer += arr[j];  
  
   return answer / i;  
}  
  
int main() {  
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
3  
```  
  
## <a name="code-example"></a>Exemple de code  
 L’exemple suivant montre comment appeler à partir de c#, une fonction de Visual C++ qui accepte un nombre variable d’arguments.  
  
```  
// mcppv2_paramarray2.cpp  
// compile with: /clr:safe /LD  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
```  
  
 La fonction `f` peut être appelée à partir de c# ou Visual Basic, par exemple, comme s’il s’agissait d’une fonction qui peut prendre un nombre variable d’arguments.  
  
 En c#, un argument est passé à un `ParamArray` paramètre peut être appelé par un nombre variable d’arguments. L’exemple de code suivant est en c#.  
  
```  
// mcppv2_paramarray3.cs  
// compile with: /r:mcppv2_paramarray2.dll  
// a C# program  
  
public class X {  
   public static void Main() {  
      // Visual C# will generate a String array to match the   
      // ParamArray attribute  
      C myc = new C();  
      myc.f("hello", "there", "world");  
   }  
}  
```  
  
 Un appel à `f` dans Visual C++ peut passer un tableau initialisé ou un tableau de longueur variable.  
  
```  
// mcpp_paramarray4.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class C {  
public:   
   void f( ... array<String^>^ a ) {}  
};  
  
int main() {  
   C ^ myc = gcnew C();  
   myc->f("hello", "world", "!!!");  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tableaux](../windows/arrays-cpp-component-extensions.md)
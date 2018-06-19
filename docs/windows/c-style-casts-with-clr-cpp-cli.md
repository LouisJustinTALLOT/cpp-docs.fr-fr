---
title: Effectue un cast de Style C avec - clr (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 384aa6d1d7a4329f52157f1d002dcda2feb5cb8a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33860396"
---
# <a name="c-style-casts-with-clr-ccli"></a>Casts de style C avec /clr (C++/CLI)
La rubrique suivante s’applique uniquement au Common Language Runtime.  
  
 Lorsqu’il est utilisé avec les types CLR, le compilateur tente de mapper de style C converti en un des conversions répertoriées ci-dessous, dans l’ordre suivant :  
  
1.  const_cast  
  
2.  safe_cast  
  
3.  safe_cast plus const_cast  
  
4.  static_cast  
  
5.  static_cast plus const_cast  
  
 Si aucun des conversions répertoriées ci-dessus est valide et si le type de l’expression et le type de cible sont des types de référence CLR, cast de style C mappe à une vérification de runtime (instruction de MSIL castclass). Sinon, un cast de style C est considéré comme non valide et que le compilateur émet une erreur.  
  
## <a name="remarks"></a>Notes  
 Un cast de style C n’est pas recommandé. Lors de la compilation avec [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), utilisez [safe_cast](../windows/safe-cast-cpp-component-extensions.md).  
  
 L’exemple suivant montre un cast de style C qui est mappé à un `const_cast`.  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 L’exemple suivant montre un cast de style C qui est mappé à un `safe_cast`.  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 L’exemple suivant montre un cast de style C qui est mappé à un `safe_cast` plus `const_cast`.  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 L’exemple suivant montre un cast de style C qui est mappé à un `static_cast`.  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 L’exemple suivant montre un cast de style C qui est mappé à un `static_cast` plus `const_cast`.  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 L’exemple suivant montre un cast de style C qui est mappé à un contrôle d’exécution.  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 L’exemple suivant montre un non valide cast de style C, ce qui entraîne le compilateur à émettre une erreur.  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)
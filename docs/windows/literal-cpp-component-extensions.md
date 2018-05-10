---
title: littéral (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
dev_langs:
- C++
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6871f02a1c37def05b6450e7ffad18f6fa45b461
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
---
# <a name="literal-c-component-extensions"></a>littéral (extensions du composant C++)
Une variable (membre de données) est marqué comme `literal` dans un **/CLR** compilation est l’équivalent natif d’un `static const` variable.  
  
## <a name="all-platforms"></a>Toutes les plateformes  
 **Remarques**  
  
 (Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)  
  
## <a name="windows-runtime"></a>Windows Runtime  
 **Remarques**  
  
 (Aucune note de cette fonctionnalité de langage ne s’applique qu’au Windows Runtime.)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
  
## <a name="remarks"></a>Notes  
 Un membre de données marqué comme `literal` doit être initialisé lorsque déclaré et la valeur doit être une constante intégrale, enum ou type chaîne. Conversion du type de l’expression d’initialisation pour le type de données-membres const static ne doit pas nécessiter une conversion définie par l’utilisateur.  
  
 Aucune mémoire est allouée pour le champ littéral lors de l’exécution ; le compilateur insère uniquement sa valeur dans les métadonnées pour la classe.  
  
 Une variable marquée `static const` ne seront pas disponibles dans les métadonnées à d’autres compilateurs.  
  
 Pour plus d’informations, consultez [statique](../cpp/storage-classes-cpp.md) et [const](../cpp/const-cpp.md).  
  
 `literal` est un mot clé contextuel. Consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md) pour plus d’informations.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre qu’un `literal` implique de variable `static`.  
  
```  
// mcppv2_literal.cpp  
// compile with: /clr  
ref struct X {  
   literal int i = 4;  
};  
  
int main() {  
   int value = X::i;  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre l’effet de littéral dans les métadonnées :  
  
```  
// mcppv2_literal2.cpp  
// compile with: /clr /LD  
public ref struct A {  
   literal int lit = 0;  
   static const int sc = 1;  
};  
```  
  
 Notez la différence dans les métadonnées pour `sc` et `lit`: le `modopt` directive est appliquée à `sc`, ce qui signifie qu’il peut être ignoré par d’autres compilateurs.  
  
```  
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```  
  
```  
.field public static literal int32 lit = int32(0x0000000A)  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant, créé en c#, référence les métadonnées créées dans l’exemple précédent et montre l’effet de `literal` et `static const` variables :  
  
```  
// mcppv2_literal3.cs  
// compile with: /reference:mcppv2_literal2.dll  
// A C# program  
class B {  
   public static void Main() {  
      // OK  
      System.Console.WriteLine(A.lit);  
      System.Console.WriteLine(A.sc);  
  
      // C# does not enforce C++ const  
      A.sc = 9;  
      System.Console.WriteLine(A.sc);  
  
      // C# enforces const for a literal  
      A.lit = 9;   // CS0131  
  
      // you can assign a C++ literal variable to a C# const variable  
      const int i = A.lit;  
      System.Console.WriteLine(i);  
  
      // but you cannot assign a C++ static const variable  
      // to a C# const variable  
      const int j = A.sc;   // CS0133  
      System.Console.WriteLine(j);  
   }  
}  
```  
  
## <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)
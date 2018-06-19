---
title: Substitutions explicites (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4eb418a6ded829e4eeeef3bf108894f9faf3d77e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879501"
---
# <a name="explicit-overrides--c-component-extensions"></a>Substitutions explicites  (extensions du composant C++)
Cette rubrique explique comment substituer explicitement un membre d’une classe de base ou une interface. Substitution nommée (explicite) doit uniquement être utilisée pour substituer une méthode par une méthode dérivée qui a un nom différent.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 **Syntaxe**  
  
```  
  
      overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **Paramètres**  
  
 *substitution de déclarateur de fonction*  
 La liste d’argument, nom et type de retour de la fonction de substitution.  Notez que la fonction de substitution ne doit pas nécessairement posséder le même nom que la fonction en cours de substitution.  
  
 *type*  
 Le type de base qui contient une fonction pour substituer.  
  
 *function*  
 Une liste délimitée par des virgules d’un ou plusieurs noms de fonction à remplacer.  
  
 *substitution de définition de fonction*  
 Les instructions de corps de fonction qui définissent la fonction de substitution.  
  
 **Remarques**  
  
 Utilisez explicite les remplacements pour créer un alias pour une signature de méthode, ou pour fournir des implémentations différentes pour les méthodes witht la même signature.  
  
 Pour plus d’informations sur la modification du comportement des types hérités et des membres de type hérité, consultez [des spécificateurs de substitution](../windows/override-specifiers-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Windows Runtime  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Remarques**  
  
 Pour plus d’informations sur explicite remplace en code natif ou code compilé avec **oldSyntax ;**, consultez [substitutions explicites](../cpp/explicit-overrides-cpp.md).  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L’exemple de code suivant montre un simple et implicite, remplacement et l’implémentation d’un membre dans une interface de base, ne pas à l’aide de substitutions explicites.  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Sortie**  
  
```Output  
X::f override of I1::f  
```  
  
 **Exemple**  
  
 L’exemple de code suivant montre comment implémenter tous les membres d’interface avec une signature commune, à l’aide de la syntaxe de substitution explicite.  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Sortie**  
  
```Output  
X::f override of I1::f and I2::f  
X::f override of I1::f and I2::f  
```  
  
 **Exemple**  
  
 L’exemple de code suivant montre comment une substitution de la fonction peut avoir un nom différent de la fonction qu’elle implémente.  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Sortie**  
  
```Output  
X::g  
```  
  
 **Exemple**  
  
 L’exemple de code suivant montre une implémentation d’interface explicite qui implémente un type de collection sans échec.  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)
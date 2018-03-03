---
title: sealed (Extensions du composant C++) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb8a8b7ea695d878235898a8741adf04ba91748c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sealed--c-component-extensions"></a>sealed  (extensions du composant C++)
`sealed` est un mot clé contextuel pour les classes ref qui indique qu'un membre virtuel ne peut pas être remplacé ou qu'un type ne peut pas être utilisé comme type de base.  
  
> [!NOTE]
>  La norme ISO C ++ 11 Standard langue a la [final](../cpp/final-specifier.md) mot clé, qui est pris en charge dans Visual Studio. Utilisez `final` sur les classes standard et `sealed` sur les classes ref.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
  
## <a name="syntax"></a>Syntaxe
  
```  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
```  
  
### <a name="parameters"></a>Paramètres  
  
 *identifier*  
 Nom de la fonction ou de la classe.  
  
 *type de retour*  
 Type retourné par une fonction.  
  
## <a name="remarks"></a>Notes  
  
 Dans le premier exemple de syntaxe, une classe est sealed. Dans le deuxième exemple, une fonction virtuelle est sealed.  
  
 Le `sealed` mot clé est valide pour les cibles natives et également pour le Windows Runtime et le common language runtime (CLR). Pour plus d’informations, consultez [des spécificateurs de substitution et Compilations natives](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Vous pouvez détecter au moment de la compilation si un type est sealed à l’aide de la `__is_sealed(type)` trait de type. Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `sealed` est un mot clé contextuel.  Pour plus d’informations, consultez [mots clés contextuels](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Windows Runtime  
 Consultez [les classes ou structures](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 (Aucune note de cette fonctionnalité de langage ne s'applique qu'au Common Language Runtime.)  
  
### <a name="requirements"></a>Configuration requise  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 L'exemple de code suivant montre l'effet de `sealed` sur un membre virtuel.  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
```Output  
X::f override of I1::f  
X::f override of I1::g  
Y::f override of I1::f  
```  
  
 L'exemple de code suivant montre comment marquer une classe comme sealed.  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)
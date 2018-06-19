---
title: Boxing (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
ms.assetid: b5fd2c98-c578-4f83-8257-6dd663478665
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f689255af653e5dfdf69250e4988aa809393461
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861355"
---
# <a name="boxing--c-component-extensions"></a>Boxing  (extensions du composant C++)
Le compilateur Visual C++ peut convertir des types valeur aux objets dans un processus appelé *boxing*et convertir les objets à des types de valeur dans un processus appelé *unboxing*.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 (Aucune remarque pour cette fonctionnalité de langage ne s’applique à tous les runtimes.)  
  
## <a name="windows-runtime"></a>Windows Runtime  
 C + c++ / CX prend en charge une syntaxe raccourcie pour les types valeur boxing et unboxing de types de référence. Un type valeur est boxed quand il est assigné à une variable de type `Object`. Une variable `Object` est unboxed quand elle est assignée à une variable de type valeur et que le type unboxed est spécifié entre parenthèses ; autrement dit, quand la variable objet est convertie en type valeur.  
  
```  
  
  Platform::Object^  
  object_variable  = value_variable;  
value_variable = (value_type) object_variable;  
  
```  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
### <a name="examples"></a>Exemples  
 L'exemple de code suivant effectue une opération boxing et une opération unboxing sur une valeur `DateTime`. Tout d'abord, l'exemple obtient une valeur DateTime qui représente la date et l'heure actuelles et l'assigne à une variable DateTime. Ensuite, une opération boxing est effectuée sur la valeur DateTime en l'assignant à une variable objet. Enfin, la valeur boxed est unboxed en l'assignant à une autre variable DateTime.  
  
 Pour tester l'exemple, créez un projet BlankApplication, remplacez la méthode BlankPage::OnNavigatedTo(), puis spécifiez les points d'arrêt au crochet fermant et l'attribution à la variable str1. Quand l'exemple atteint le crochet fermant, examinez str1.  
  
```  
  
void BlankPage::OnNavigatedTo(NavigationEventArgs^ e)  
{  
    using namespace Windows::Globalization::DateTimeFormatting;  
  
    Windows::Foundation::DateTime dt, dtAnother;  
    Platform::Object^ obj1;  
  
    Windows::Globalization::Calendar^ c =   
        ref new Windows::Globalization::Calendar;  
    c->SetToNow();  
    dt = c->GetDateTime();  
    auto dtf = ref new DateTimeFormatter(  
                           YearFormat::Full,   
                           MonthFormat::Numeric,   
                           DayFormat::Default,   
                           DayOfWeekFormat::None);  
    String^ str1 = dtf->Format(dt);  
    OutputDebugString(str1->Data());  
    OutputDebugString(L"\r\n");  
  
    // Box the value type and assign to a reference type.  
    obj1 = dt;  
    // Unbox the reference type and assign to a value type.  
    dtAnother = (Windows::Foundation::DateTime) obj1;  
  
    // Format the DateTime for display.  
    String^ str2 = dtf->Format(dtAnother);  
    OutputDebugString(str2->Data());  
}  
  
```  
  
 Pour plus d’informations, consultez [Boxing (C + c++ / CX)](http://msdn.microsoft.com/library/windows/apps/hh969554.aspx).  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 Le compilateur Visual C++ effectue maintenant un boxing des types valeur en <xref:System.Object>.  Cette opération est possible en raison d'une conversion définie par le compilateur pour convertir des types valeur en <xref:System.Object>.  
  
 Les opérations boxing et unboxing permettent de traiter les types valeur en tant qu'objets. Les types valeur, y compris les types struct et les types intégrés comme int, peuvent être convertis en et à partir du type <xref:System.Object>.  
  
 Pour plus d'informations, voir :  
  
-   [Guide pratique pour demander explicitement le boxing](../dotnet/how-to-explicitly-request-boxing.md)  
  
-   [Guide pratique pour utiliser gcnew pour créer des types valeur et utiliser un boxing implicite](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)  
  
-   [Guide pratique pour effectuer une conversion unbox](../dotnet/how-to-unbox.md)  
  
-   [Conversions standard et boxing implicite](../dotnet/standard-conversions-and-implicit-boxing.md)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L'exemple suivant montre comment fonctionne le boxing implicite.  
  
```cpp  
// vcmcppv2_explicit_boxing2.cpp  
// compile with: /clr  
using namespace System;  
  
ref class A {  
public:  
   void func(System::Object^ o){Console::WriteLine("in A");}  
};  
  
value class V {};  
  
interface struct IFace {  
   void func();  
};  
  
value class V1 : public IFace {  
public:  
   virtual void func() {  
      Console::WriteLine("Interface function");  
   }  
};  
  
value struct V2 {  
   // conversion operator to System::Object  
   static operator System::Object^(V2 v2) {  
      Console::WriteLine("operator System::Object^");  
      return (V2^)v2;  
   }  
};  
  
void func1(System::Object^){Console::WriteLine("in void func1(System::Object^)");}  
void func1(V2^){Console::WriteLine("in func1(V2^)");}  
  
void func2(System::ValueType^){Console::WriteLine("in func2(System::ValueType^)");}  
void func2(System::Object^){Console::WriteLine("in func2(System::Object^)");}  
  
int main() {  
   // example 1 simple implicit boxing  
   Int32^ bi = 1;  
   Console::WriteLine(bi);  
  
   // example 2 calling a member with implicit boxing  
   Int32 n = 10;  
   Console::WriteLine("xx = {0}", n.ToString());  
  
   // example 3 implicit boxing for function calls  
   A^ a = gcnew A;  
   a->func(n);  
  
   // example 4 implicit boxing for WriteLine function call  
   V v;  
   Console::WriteLine("Class {0} passed using implicit boxing", v);  
   Console::WriteLine("Class {0} passed with forced boxing", (V^)(v));   // force boxing  
  
   // example 5 casting to a base with implicit boxing  
   V1 v1;  
   IFace ^ iface = v1;  
   iface->func();  
  
   // example 6 user-defined conversion preferred over implicit boxing for function-call parameter matching  
   V2 v2;  
   func1(v2);   // user defined conversion from V2 to System::Object preferred over implicit boxing  
                // Will call void func1(System::Object^);  
  
   func2(v2);   // OK: Calls "static V2::operator System::Object^(V2 v2)"  
   func2((V2^)v2);   // Using explicit boxing: calls func2(System::ValueType^)  
}  
```  
  
 **Sortie**  
  
```Output  
1  
  
xx = 10  
  
in A  
  
Class V passed using implicit boxing  
  
Class V passed with forced boxing  
  
Interface function  
  
in func1(V2^)  
  
in func2(System::ValueType^)  
  
in func2(System::ValueType^)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)
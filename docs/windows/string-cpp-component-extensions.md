---
title: Chaîne (Extensions du composant C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfab95c400aad949f06a559fffbdb42993910bb7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889239"
---
# <a name="string--c-component-extensions"></a>Chaîne  (extensions du composant C++)
Le compilateur Visual C++ prend en charge *chaînes*, qui sont des objets qui représentent le texte comme une séquence de caractères. Visual C++ prend en charge les variables de chaîne, dont la valeur est implicite, et les littéraux, dont la valeur est une chaîne entre guillemets explicite.  
  
## <a name="all-runtimes"></a>Tous les runtimes  
 Le Windows Runtime et le common language runtime représentent les chaînes en tant qu’objets dont la mémoire allouée est gérée automatiquement. Autrement dit, vous ne sont pas obligé d’ignorer explicitement la mémoire pour une chaîne lorsque le passage de variable chaîne hors de portée ou votre application se termine. Pour indiquer que la durée de vie d’un objet string est géré automatiquement, déclarez le type de chaîne avec la [handle-to-object (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md) modificateur.  
  
## <a name="windows-runtime"></a>Windows Runtime  
 L’architecture de Windows Runtime nécessite Visual C++ implémenter le `String` de type de données dans le `Platform` espace de noms. Pour des raisons pratiques, Visual C++ fournit aussi la `string` de type de données, qui est un synonyme de `Platform::String`, dans le `default` espace de noms.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
// compile with /ZW  
using namespace Platform;  
using namespace default;  
   Platform::String^ MyString1 = "The quick brown fox";  
   String^ MyString2 = "jumped over the lazy dog.";  
   String^ MyString3 = "Hello, world!";  
  
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations et des exemples sur les chaînes, consultez [Platform::String, std::wstring et littéraux (plate-forme)](http://msdn.microsoft.com/en-us/ec92fbc6-edf3-4137-a85e-8e29bdb857a8)  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 Cette rubrique explique comment le compilateur Visual C++ traite les littéraux de chaîne lorsque vous l’exécutez à l’aide de la **/CLR** option du compilateur. Pour utiliser **/CLR**, vous devez également utiliser le common language runtime (CLR), C + c++ / syntaxe CLI et les objets gérés. Pour plus d’informations sur **/CLR**, consultez [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Lors de la compilation avec **/CLR**, le compilateur convertit des littéraux de chaîne en chaînes de type <xref:System.String>. Pour conserver la compatibilité descendante avec le code existant sont deux exceptions à cela :  
  
-   Gestion des exceptions. Lorsqu’un littéral de chaîne est levé, le compilateur intercepte comme un littéral de chaîne.  
  
-   Déduction du modèle. Lorsqu’un littéral de chaîne est passé comme argument de modèle, le compilateur ne convertira pas à un <xref:System.String>. Notez que les littéraux de chaîne passées comme argument générique seront promus à <xref:System.String>.  
  
 Le compilateur a également une prise en charge intégrée pour les trois opérateurs, que vous pouvez substituer pour personnaliser leur comportement :  
  
-   System::String ^ (opérateur) + (System::String, System::String) ;  
  
-   System::String ^ (opérateur) + (System::Object, System::String) ;  
  
-   System::String ^ (opérateur) + (System::String, System::Object) ;  
  
 Lorsqu’il est passé un <xref:System.String>, le compilateur zone, si nécessaire et puis concaténer l’objet (avec ToString) avec la chaîne.  
  
> [!NOTE]
>  Le point d’insertion (« ^ ») indique que la variable déclarée est un handle vers un C + c++ / CLI d’objet managé.  
  
 Pour plus d’informations, consultez [littéraux de chaîne et caractère](../cpp/string-and-character-literals-cpp.md).  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 L’exemple de code suivant illustre la concaténation et comparaison de chaînes.  
  
```cpp  
// string_operators.cpp  
// compile with: /clr  
// In the following code, the caret ("^") indicates that the   
// declared variable is a handle to a C++/CLI managed object.  
using namespace System;  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   // variables of System::String returning a System::String  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   // accessing a character in the string  
   Console::WriteLine(a[2]);  
  
   // concatenation of three System::Strings  
   Console::WriteLine(a + b + c);  
  
   // concatenation of a System::String and string literal  
   Console::WriteLine(a + "zzz");  
  
   // you can append to a System::String ^  
   Console::WriteLine(a + 1);  
   Console::WriteLine(a + 'a');  
   Console::WriteLine(a + 3.1);  
  
   // test System::String ^ for equality  
   a += b;  
   Console::WriteLine(a);  
   a = b;  
   if (a == b)  
      Console::WriteLine("a and b are equal");  
  
   a = "abc";  
   if (a != b)  
      Console::WriteLine("a and b are not equal");  
  
   // System:String ^ and tracking reference  
   String^% rstr1 = a;  
   Console::WriteLine(rstr1);  
  
   // testing an empty System::String ^  
   String ^ n;  
   if (n == nullptr)  
      Console::WriteLine("n is empty");  
}  
```  
  
 **Sortie**  
  
```Output  
abcdef  
  
abcghi  
  
ghiabc  
  
c  
  
abcdefghi  
  
abczzz  
  
abc1  
  
abc97  
  
abc3.1  
  
abcdef  
  
a and b are equal  
  
a and b are not equal  
  
abc  
  
n is empty  
```  
  
 **Exemple**  
  
 L’exemple suivant montre que vous pouvez surcharger les opérateurs fournis par le compilateur, et que le compilateur ne recherche pas une surcharge de fonction basée sur le <xref:System.String> type.  
  
```cpp  
// string_operators_2.cpp  
// compile with: /clr  
using namespace System;  
  
// a string^ overload will be favored when calling with a String  
void Test_Overload(const char * a) {   
   Console::WriteLine("const char * a");   
}  
void Test_Overload(String ^ a) {   
   Console::WriteLine("String ^ a");   
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, String ^ b) {  
   return ("overloaded +(String ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(Object ^ a, String ^ b) {  
   return ("overloaded +(Object ^ a, String ^ b)");  
}  
  
// overload will be called instead of compiler defined operator  
String ^ operator +(String ^ a, Object ^ b) {  
   return ("overloaded +(String ^ a, Object ^ b)");  
}  
  
int main() {  
   String ^ a = gcnew String("abc");  
   String ^ b = "def";   // same as gcnew form  
   Object ^ c = gcnew String("ghi");  
  
   char d[100] = "abc";  
  
   Console::WriteLine(a + b);  
   Console::WriteLine(a + c);  
   Console::WriteLine(c + a);  
  
   Test_Overload("hello");  
   Test_Overload(d);  
}  
```  
  
 **Sortie**  
  
```Output  
overloaded +(String ^ a, String ^ b)   
  
overloaded +(String ^ a, Object ^ b)   
  
overloaded +(Object ^ a, String ^ b)   
  
String ^ a  
  
const char * a  
```  
  
 **Exemple**  
  
 L’exemple suivant montre que le compilateur fait la distinction entre les chaînes d’origine et <xref:System.String> chaînes.  
  
```cpp  
// string_operators_3.cpp  
// compile with: /clr  
using namespace System;  
int func() {  
   throw "simple string";   // const char *  
};  
  
int func2() {  
   throw "string" + "string";   // returns System::String  
};  
  
template<typename T>  
void func3(T t) {  
   Console::WriteLine(T::typeid);  
}  
  
int main() {  
   try {  
      func();  
   }  
   catch(char * e) {  
      Console::WriteLine("char *");  
   }  
  
   try {  
      func2();  
   }  
   catch(String^ str) {  
      Console::WriteLine("String^ str");  
   }  
  
   func3("string");   // const char *  
   func3("string" + "string");   // returns System::String  
}  
```  
  
 **Sortie**  
  
```Output  
char *  
  
String^ str  
  
System.SByte*  
  
System.String  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)   
 [Littéraux de chaîne et caractères](../cpp/string-and-character-literals-cpp.md)   
 [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)
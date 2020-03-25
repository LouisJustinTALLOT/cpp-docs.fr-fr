---
title: Chaîne (C++/CLI et C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: b9da900ffbfff34dc596d8981095d8285bf37208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171942"
---
# <a name="string--ccli-and-ccx"></a>Chaîne (C++/CLI et C++/CX)

Le Windows Runtime et le common language runtime représentent des chaînes en tant qu’objets dont la mémoire allouée est gérée automatiquement. Autrement dit, vous n’êtes pas obligé d’ignorer explicitement la mémoire d’une chaîne lorsque la variable de chaîne devient hors de portée ou que votre application se termine. Pour indiquer que la durée de vie d’un objet chaîne doit être gérée automatiquement, déclarez le type de chaîne avec le modificateur [handle-to-object (^)](handle-to-object-operator-hat-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows Runtime

L’architecture Windows Runtime nécessite que le type de données `String` se trouve dans l’espace de noms `Platform`. Pour des raisons pratiques, Visual C++ fournit également le type de données `string`, qui est un synonyme de `Platform::String`, dans l’espace de noms `default`.

### <a name="syntax"></a>Syntaxe

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Lors de la compilation avec `/clr`, le compilateur convertit des littéraux de chaîne en chaînes de type <xref:System.String>. Pour conserver la compatibilité descendante avec le code existant, il existe deux exceptions :

- Gestion des exceptions. Lorsqu’un littéral de chaîne est généré, le compilateur l’intercepte en tant que littéral de chaîne.

- Déduction des modèles. Lorsqu’un littéral de chaîne est transmis en tant qu’argument de modèle, le compilateur ne le convertit pas en <xref:System.String>. Notez que les littéraux de chaîne passés comme argument générique sont promus en <xref:System.String>.

Le compilateur possède également une prise en charge intégrée pour les trois opérateurs, que vous pouvez remplacer pour personnaliser leur comportement :

- Opérateur System::String^ + (System::String, System::String) ;

- Opérateur System::String^ + (System::Object, System::String) ;

- Opérateur System::String^ + (System::String, System::Object) ;

Quand un <xref:System.String> est transmis, le compilateur convertit, si nécessaire, puis concatène l’objet (avec ToString) avec la chaîne.

> [!NOTE]
> Le signe insertion (« ^ ») indique que la variable déclarée est un descripteur pour l’objet managé C++/CLI.

Pour plus d’informations, consultez [Littéraux de chaîne et de caractère](../cpp/string-and-character-literals-cpp.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : **/clr**

### <a name="examples"></a>Exemples

L’exemple de code suivant illustre la concaténation et la comparaison de chaînes.

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

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

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

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

L’exemple suivant montre que vous pouvez surcharger les opérateurs fournis par le compilateur et que le compilateur recherche une surcharge de fonction basée sur le type <xref:System.String>.

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

L’exemple suivant montre que le compilateur fait la distinction entre les chaînes natives et les chaînes <xref:System.String>.

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

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[Littéraux de chaîne et de caractère](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md)

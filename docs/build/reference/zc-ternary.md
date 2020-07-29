---
title: /Zc:ternary (Appliquer les règles d’opérateur conditionnel)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 04bd0c49528d86ddd4d1e6c77804cf64278db188
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211877"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>`/Zc:ternary`(Appliquer les règles d’opérateur conditionnelles)

Activez l’application des règles standard C++ pour les types et la qualification const ou volatile (CV) des deuxième et troisième opérandes dans une expression d’opérateur conditionnel.

## <a name="syntax"></a>Syntaxe

> **`/Zc:ternary`**[**`-`**]

## <a name="remarks"></a>Notes

À compter de Visual Studio 2017, le compilateur prend en charge le comportement de l' *opérateur conditionnel* standard C++ ( **`?:`** ). Il est également connu sous le nom d' *opérateur ternaire*. La norme C++ exige que les opérandes ternaires répondent à l’une des trois conditions suivantes : les opérandes doivent être du même type et de la même **`const`** **`volatile`** qualification (CV-qualification), ou un seul opérande doit être convertible de manière non ambiguë en tant que autre type et CV-qualification. Ou bien, l’un des opérandes ou les deux doivent être une expression throw. Dans les versions antérieures à Visual Studio 2017 version 15,5, le compilateur permettait des conversions qui sont considérées comme ambiguës par la norme.

Lorsque l' **`/Zc:ternary`** option est spécifiée, le compilateur est conforme à la norme. Elle rejette le code qui ne respecte pas les règles pour les types correspondants et la qualification CV des deuxième et troisième opérandes.

L' **`/Zc:ternary`** option est désactivée par défaut dans Visual Studio 2017. Utilisez **`/Zc:ternary`** pour activer le comportement de conformité, ou **`/Zc:ternary-`** pour spécifier explicitement le comportement de compilateur non conforme précédent. L' [`/permissive-`](permissive-standards-conformance.md) option active implicitement cette option, mais elle peut être substituée à l’aide de **`/Zc:ternary-`** .

### <a name="examples"></a>Exemples

Cet exemple montre comment une classe qui fournit à la fois une initialisation non explicite à partir d’un type et une conversion vers un type peut entraîner des conversions ambiguës. Ce code est accepté par le compilateur par défaut, mais rejeté quand **/`Zc:ternary`** ou **`/permissive-`** est spécifié.

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

Pour corriger ce code, effectuez un cast explicite en type commun préféré ou évitez un sens de conversion de type. Vous pouvez conserver le compilateur pour qu’il corresponde à une conversion de type en rendant la conversion explicite.

Une exception importante à ce modèle courant est lorsque le type des opérandes est l’un des types de chaînes terminées par le caractère null, comme `const char*` , `const char16_t*` , et ainsi de suite. Vous pouvez également reproduire l’effet avec les types de tableau et les types de pointeurs qu’il atténue. Le comportement lorsque le deuxième ou le troisième opérande réel `?:` est un littéral de chaîne de type correspondant dépend de la norme de langage utilisée. C++ 17 a modifié la sémantique pour ce cas à partir de C++ 14. Par conséquent, le compilateur accepte le code dans l’exemple suivant sous la valeur par défaut **`/std:c++14`** , mais le rejette quand vous spécifiez **`/std:c++17`** .

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

Pour corriger ce code, effectuez un cast explicite de l’un des opérandes.

Sous **`/Zc:ternary`** , le compilateur rejette les opérateurs conditionnels où l’un des arguments est de type **`void`** et l’autre n’est pas une **`throw`** expression. Ce modèle est couramment utilisé dans les macros de type assertion :

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

La solution classique consiste à remplacer l’argument non void par `void()` .

Cet exemple montre le code qui génère une erreur sous **`/Zc:ternary`** et **`/Zc:ternary-`** :

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

Ce code a précédemment donné cette erreur :

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Avec **`/Zc:ternary`** , la raison de l’échec devient plus claire. L’une des différentes conventions d’appel définies par l’implémentation peut être utilisée pour générer chaque lambda. Toutefois, le compilateur n’a pas de règle de préférence pour lever l’ambiguïté des signatures lambda possibles. La nouvelle sortie ressemble à ceci :

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Une source courante de problèmes détectés par **`/Zc:ternary`** provient des opérateurs conditionnels utilisés dans la programmation méta des modèles. Certains des types de résultats changent sous ce commutateur. L’exemple suivant illustre deux cas où **`/Zc:ternary`** modifie le type de résultat d’une expression conditionnelle dans un contexte de non-programmation :

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

La solution la plus courante consiste à appliquer une `std::remove_reference` caractéristique sur le type de résultat, si nécessaire pour conserver l’ancien comportement.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure **`/Zc:ternary`** ou **`/Zc:ternary-`** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[`/Zc`Conformité](zc-conformance.md)

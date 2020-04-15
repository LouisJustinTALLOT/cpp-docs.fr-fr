---
title: /Zc:ternary (Appliquer les règles d’opérateur conditionnel)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 7c95f061e195ccf7fef8a6a21d193b257baa5f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335676"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (Appliquer les règles d’opérateur conditionnel)

Permettre l’application des règles standard de C pour les types et la qualification const ou volatile (cv) des deuxième et troisième opérandes dans une expression d’opérateur conditionnel.

## <a name="syntax"></a>Syntaxe

> **/Zc:ternary****-**[ ]

## <a name="remarks"></a>Notes

À partir de Visual Studio 2017, le compilateur prend en charge *l’opérateur conditionnel* standard CMD **(?:**) comportement. Il est également connu comme *l’opérateur ternaire*. La norme C exige que les opérandes ternaires satisfont à l’une des trois conditions : les opérandes doivent être du même type et **la même const** ou la qualification **volatile** (cv-qualification), ou un seul opérande doit être sans ambiguïté convertible au même type et cv-qualification que l’autre. Ou, un ou les deux opérands doivent être une expression de jet. Dans les versions avant Visual Studio 2017 version 15.5, le compilateur a permis des conversions qui sont considérées comme ambigus par la norme.

Lorsque l’option **/Zc:ternary** est spécifiée, le compilateur est conforme à la norme. Il rejette le code qui ne satisfait pas aux règles pour les types appariés et la qualification cv des deuxième et troisième opérands.

**L’option /Zc:ternary** est éteinte par défaut dans Visual Studio 2017. Utilisez **/Zc:ternary** pour permettre un comportement conforme, ou **/Zc:ternary-** pour spécifier explicitement le comportement compilateur non conforme précédent. [L’option /permissive-](permissive-standards-conformance.md) permet implicitement cette option, mais elle peut être remplacée par l’utilisation **de /Zc:ternary-**.

### <a name="examples"></a>Exemples

Cet exemple montre comment une classe qui fournit à la fois une initialisation non explicite à partir d’un type, et la conversion en un type, peut conduire à des conversions ambigues. Ce code est accepté par le compilateur par défaut, mais rejeté lorsque **/Zc:ternary** ou **/permissive-** est spécifié.

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

Pour corriger ce code, faites un casting explicite au type commun préféré, ou empêchez une direction de conversion de type. Vous pouvez empêcher le compilateur d’assortir une conversion de type en rendant la conversion explicite.

Une exception importante à ce modèle commun est quand le type des opérands `const char*`est `const char16_t*`l’un des types de cordes non-licenciés, tels que , , et ainsi de suite. Vous pouvez également reproduire l’effet avec les types de tableau et les types de pointeurs qu’ils se décomposent. Le comportement lorsque le deuxième ou `?:` troisième opératoire réel est une chaîne littérale de type correspondant dépend de la norme de langue utilisée. Le C-17 a changé de sémantique pour ce cas à partir de C 14. En conséquence, le compilateur accepte le code dans l’exemple suivant sous la par défaut **/std: c '14**, mais le rejette lorsque vous spécifiez **/std:c '17**.

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

Pour corriger ce code, lancez explicitement l’un des opérands.

Sous **/Zc:ternary**, le compilateur rejette les opérateurs conditionnels où l’un des arguments est de type **vide**, et l’autre n’est pas une expression de lancer. Une utilisation commune de ce modèle est dans les macros ASSERT-like :

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

La solution typique est de remplacer `void()`l’argument non nul par .

Cet exemple montre le code qui génère une erreur sous **/Zc:ternary** et **/Zc:ternary-**:

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

Ce code a déjà donné cette erreur:

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Avec **/Zc:ternary**, la raison de l’échec devient plus claire. N’importe lequel de plusieurs conventions d’appel définies par la mise en œuvre pourrait être utilisée pour générer chaque lambda. Cependant, le compilateur n’a pas de règle de préférence pour désambiguer les signatures de lambda possibles. La nouvelle sortie ressemble à ceci:

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Une source commune de problèmes trouvés par **/Zc:ternary provient d’opérateurs** conditionnels utilisés dans la méta-programmation de modèles. Certains types de résultats changent sous ce commutateur. L’exemple suivant montre deux cas où **/Zc:ternary** modifie le type de résultat d’une expression conditionnelle dans un contexte non-métaprogramme :

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

Le correctif typique est `std::remove_reference` d’appliquer un trait sur le type de résultat, si nécessaire pour préserver l’ancien comportement.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page propriété **Configuration Properties** > **C/CMD** > **Command Line.**

1. Modifier la propriété **Options supplémentaires** pour inclure **/Zc:ternary** ou **/Zc:ternary-** et puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)

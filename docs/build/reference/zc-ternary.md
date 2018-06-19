---
title: /Zc:ternary (appliquer les règles opérateur conditionnel) | Documents Microsoft
ms.date: 3/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:ternary
dev_langs:
- C++
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
author: corob-msft
ms.author: corob
ms.openlocfilehash: 613381795fb962e1f10ec01598748b617b7543aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380821"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (appliquer les règles opérateur conditionnel)

Activer la mise en œuvre de règles Standard C++ pour les types et const ou volatile qualification (VC) des deuxième et troisième opérandes dans une expression de l’opérateur conditionnel.

## <a name="syntax"></a>Syntaxe

> **/Zc:ternary**[**-**]

## <a name="remarks"></a>Notes

Visual Studio version 15.3 permet la prise en charge du compilateur pour l’opérateur C++ (ou conditionnel ternaire) standard (**? :**) comportement. La norme C++ requiert des opérandes doit être du même type et cv-qualification, ou pour qu’un seul opérande puisse être converti sans ambiguïté sur le même type et cv-qualification en tant que l’autre ou pour un ou deux opérandes d’une expression throw. Dans les versions antérieures de Visual Studio version 15.5, le compilateur a autorisé les conversions qui sont considérés comme étant ambiguës par la norme. Lorsque le **/Zc:ternary** est spécifiée, le compilateur est conforme à la norme et refuse le code qui ne satisfait pas les règles de mise en correspondance des types et les cv-qualification des deuxième et troisième opérandes.

Le **/Zc:ternary** option est désactivée par défaut. Utilisez **/Zc:ternary** pour activer le comportement conforme, ou **/Zc:ternary-** pour spécifier explicitement le comportement de compilateur précédent non conforme. Le [/ permissive-](permissive-standards-conformance.md) implicitement permet de cette option, mais elle peut être substituée à l’aide de **/Zc:ternary-**.

### <a name="examples"></a>Exemples

Cet exemple montre comment une classe qui fournit les deux une initialisation non explicite à partir d’un type et une conversion vers un type peut entraîner des conversions ambiguës. Ce code est accepté par le compilateur par défaut, mais refusés lorsque **/Zc:ternary** ou **/ permissive-** est spécifié.

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

Le correctif requis consiste à effectuer une conversion explicite en un type commun par défaut, ou empêcher un sens de conversion de la participation à la recherche du compilateur pour une correspondance de type en effectuant la conversion explicite.

Une exception importante à ce modèle commun est lorsque le type des opérandes est un des types de chaîne terminée par null, tel que `const char*`, `const char16_t*`, et ainsi de suite. Vous pouvez également reproduire ce avec les types de tableau et les types de pointeur qu’ils s’atténuer à. Le comportement lorsque le réel deuxième ou troisième opérande ? : un littéral de chaîne de type correspondant varie selon la norme du langage utilisé. C ++ 17 a modifié la sémantique pour ce cas de C ++ 14. Par conséquent, le code dans l’exemple suivant est accepté sous **/std : c ++ 14** (la valeur par défaut du compilateur), mais est rejeté lorsque **/std : c ++ 17** est spécifié.

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

Pour corriger ce code, convertir explicitement un des opérandes.

Sous **/Zc:ternary**, les compilateur rejette des opérateurs conditionnels où un des arguments est de type void, et l’autre n’est pas une expression throw. Une utilisation courante de ces est dans les macros d’assertion de type :

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

La solution classique consiste simplement à remplacer l’argument non void avec void().

Cet exemple montre le code qui génère une erreur dans les répertoires **/Zc:ternary** et **/Zc:ternary-**:

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

Ce code a déjà donné cette erreur :

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

Avec **/Zc:ternary** la raison de l’échec devient plus claire ; sur les architectures où une des conventions d’appel plusieurs défini par l’implémentation peut être utilisée pour générer chaque expression lambda, le compilateur n’exprime aucune préférence entre eux qui peut lever l’ambiguïté entre les signatures lambda possible. La nouvelle sortie ressemble à ceci :

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

Une source fréquente de problèmes liés à l’adoption de **/Zc:ternary** provient de l’utilisation de l’opérateur conditionnel dans le modèle méta programmation, car certains types de résultats de changent de ce commutateur. L’exemple suivant illustre les deux cas où **/Zc:ternary** modifie le type de résultat d’une expression conditionnelle dans un contexte de la programmation de métadonnées :

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

La résolution standard dans ce cas consiste à appliquer un `std::remove_reference` caractéristique du résultat de type quand cela est nécessaire afin de préserver l’ancien comportement.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zc:ternary** ou **/Zc:ternary-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)  

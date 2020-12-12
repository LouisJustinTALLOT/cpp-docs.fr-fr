---
description: 'En savoir plus sur:/Zc : rvalueCast (appliquer les règles de conversion de type)'
title: /Zc:rvalueCast (Appliquer les règles de conversion de type)
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: f9739f16b12e5e0335f17bb5a56ed1e4aa265e9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269144"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Appliquer les règles de conversion de type)

Lorsque l' **`/Zc:rvalueCast`** option est spécifiée, le compilateur identifie correctement un type de référence rvalue comme le résultat d’une opération de conversion. Son comportement est conforme à la norme C++ 11. Lorsque l’option n’est pas spécifiée, le comportement du compilateur est le même que dans Visual Studio 2012.

## <a name="syntax"></a>Syntaxe

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>Notes

Si **`/Zc:rvalueCast`** est spécifié, le compilateur suit la section 5,4 de la norme c++ 11 et traite uniquement les expressions de cast qui génèrent des types non-référence et les expressions de cast qui génèrent des références rvalue aux types sans fonction en tant que types rvalue. Par défaut, ou si **`/Zc:rvalueCast-`** est spécifié, le compilateur est non conforme et traite toutes les expressions de cast qui génèrent des références rvalue en tant que rvalues. Pour la conformité et pour éliminer les erreurs lors de l’utilisation de casts, nous vous recommandons d’utiliser **`/Zc:rvalueCast`** .

Par défaut, **`/Zc:rvalueCast`** est désactivé ( **`/Zc:rvalueCast-`** ). L’option de compilateur [/permissive-](permissive-standards-conformance.md) définit implicitement cette option, mais elle peut être substituée à l’aide de **`/Zc:rvalueCast-`** .

Utilisez **`/Zc:rvalueCast`** si vous transmettez une expression de cast en tant qu’argument à une fonction qui accepte un type référence rvalue. Le comportement par défaut provoque une erreur du compilateur [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) lorsque le compilateur détermine de manière incorrecte le type de l’expression de cast. Cet exemple montre une erreur du compilateur dans le code correct lorsque **`/Zc:rvalueCast`** n’est pas spécifié :

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

Le comportement par défaut du compilateur peut ne pas signaler l'erreur C2102 quand cela est nécessaire. Dans cet exemple, le compilateur ne signale pas d’erreur si l’adresse d’une rvalue créée par un cast d’identité est prise lorsque **`/Zc:rvalueCast`** n’est pas spécifié :

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés de la propriété de **configuration**  >  **C/C++**  >  **Language** .

1. Affectez à la propriété **appliquer les règles de conversion de type** la valeur **`/Zc:rvalueCast`** ou **`/Zc:rvalueCast-`** . Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)

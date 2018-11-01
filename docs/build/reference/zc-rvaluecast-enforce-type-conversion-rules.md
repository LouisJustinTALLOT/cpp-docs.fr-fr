---
title: /Zc:rvalueCast (Appliquer les règles de conversion de type)
ms.date: 03/06/2018
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
ms.openlocfilehash: 8e4be80d09ebf7f48795e01669610a0dc4f736d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648199"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (Appliquer les règles de conversion de type)

Lorsque le **/Zc : rvaluecast** est spécifiée, le compilateur identifie correctement un type référence rvalue comme résultat d’une opération de cast conformément à la norme C ++ 11. Quand l'option n'est pas spécifiée, le comportement du compilateur est le même que dans Visual Studio 2012.

## <a name="syntax"></a>Syntaxe

> **/Zc:rvalueCast**[**-**]

## <a name="remarks"></a>Notes

Si **/Zc : rvaluecast** est spécifié, le compilateur suit la section 5.4 de la norme C ++ 11 et traite uniquement les expressions de types sans référence et expressions de cast qui génèrent des références rvalue à des types sans fonction cast en tant que types rvalue. Par défaut, ou si **/Zc:rvalueCast-** est spécifié, le compilateur est non conforme et traite toutes les expressions de cast qui génèrent des références rvalue comme rvalues. Pour la conformité et à éliminer les erreurs dans l’utilisation des casts, nous vous recommandons d’utiliser **/Zc : rvaluecast**.

Par défaut, **/Zc : rvaluecast** est désactivée (**/Zc:rvalueCast-**). Le [/ permissive-](permissive-standards-conformance.md) option du compilateur définit implicitement cette option, mais elle peut être substituée à l’aide de **/Zc:rvalueCast-**.

Utilisez **/Zc : rvaluecast** si vous passez une expression de cast en tant qu’argument à une fonction qui accepte un type référence rvalue. Le comportement par défaut provoque l’erreur du compilateur [l’erreur C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) lorsque le compilateur détermine de façon incorrecte le type de l’expression de cast. Cet exemple montre une erreur du compilateur adapté code lorsque **/Zc : rvaluecast** n’est pas spécifié :

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

Le comportement par défaut du compilateur peut ne pas signaler l'erreur C2102 quand cela est nécessaire. Dans cet exemple, le compilateur ne signale pas d’erreur si l’adresse d’une rvalue créée par un cast d’identité est acceptée quand **/Zc : rvaluecast** n’est pas spécifié :

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : rvaluecast** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>

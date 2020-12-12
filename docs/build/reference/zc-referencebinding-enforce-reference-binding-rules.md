---
description: 'En savoir plus sur:/Zc : referenceBinding (appliquer les règles de liaison de référence)'
title: /Zc:referenceBinding (Appliquer les règles de liaison de références)
ms.date: 03/06/2018
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
ms.openlocfilehash: 7d094a2ec3ec680c463a7a756e70e02b9c40c07c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269157"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (Appliquer les règles de liaison de références)

Lorsque l’option **/Zc : referenceBinding** est spécifiée, le compilateur n’autorise pas la liaison d’une référence lvalue non-const à un temporaire.

## <a name="syntax"></a>Syntaxe

> **/Zc : referenceBinding**[ **-** ]

## <a name="remarks"></a>Notes

Si **/Zc : referenceBinding** est spécifié, le compilateur suit la section 8.5.3 de la norme c++ 11 : il n’autorise pas les expressions qui lient un type défini par l’utilisateur à une référence lvalue non-const. Par défaut, ou si **/Zc : referenceBinding-** est spécifié, le compilateur autorise ces expressions comme une extension Microsoft, mais un avertissement de niveau 4 est émis. Pour la sécurité du code, la portabilité et la conformité, nous vous recommandons d’utiliser **/Zc : referenceBinding**.

L’option **/Zc : referenceBinding** est désactivée par défaut. L’option de compilateur [/permissive-](permissive-standards-conformance.md) définit implicitement cette option, mais elle peut être substituée à l’aide de **/Zc : referenceBinding-**.

## <a name="example"></a>Exemple

Cet exemple montre l’extension Microsoft qui permet de lier une variable temporaire d’un type défini par l’utilisateur à une référence lvalue non-const.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

int main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : referenceBinding** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>

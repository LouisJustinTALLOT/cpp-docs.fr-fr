---
title: '/ Zc : referencebinding (appliquer les règles de liaison aux références)'
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
ms.openlocfilehash: baf2106f015a4e8557cb8469d300709694e06d84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428325"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/ Zc : referencebinding (appliquer les règles de liaison aux références)

Lorsque le **/Zc : referencebinding** est spécifiée, le compilateur n’autorise pas une référence non const lvalue à lier à une table temporaire.

## <a name="syntax"></a>Syntaxe

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Notes

Si **/Zc : referencebinding** est spécifié, le compilateur suit la section 8.5.3 de la norme C ++ 11 et n’autorise pas les expressions qui lient un type défini par l’utilisateur temporaire à une référence non const lvalue. Par défaut, ou si **/Zc:referenceBinding-** n’est spécifié, le compilateur autorise de telles expressions comme une extension de Microsoft, mais un avertissement de niveau 4. Pour la sécurité du code, la portabilité et la conformité, nous vous recommandons d’utiliser **/Zc : referencebinding**.

Le **/Zc : referencebinding** option est désactivée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option du compilateur définit implicitement cette option, mais elle peut être substituée à l’aide de **/Zc:referenceBinding-**.

## <a name="example"></a>Exemple

Cet exemple montre l’extension Microsoft qui permet à une table temporaire d’un type défini par l’utilisateur doit être lié à une référence non const lvalue.

```cpp
// zcreferencebinding.cpp
struct S {
};

void f(S&) {
}

S g() {
    return S{};
}

void main() {
    S& s = g();         // warning C4239 at /W4
    const S& cs = g();  // okay, bound to const ref
    f(g());             // Extension: error C2664 only if /Zc:referenceBinding
}
```

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc : referencebinding** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>

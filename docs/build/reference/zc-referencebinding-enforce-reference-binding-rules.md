---
title: /Zc:referenceBinding (appliquer les règles de liaison aux référence) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- referenceBinding
- /Zc:referenceBinding
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- referenceBinding
- Enforce reference binding rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 0c6cfaac-9c2a-41a3-aa94-64ca8ef261fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30038f6ff73eaa2d9536c3685927458a70209864
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378878"
---
# <a name="zcreferencebinding-enforce-reference-binding-rules"></a>/Zc:referenceBinding (appliquer les règles de liaison aux référence)

Lorsque le **/Zc:referenceBinding** est spécifiée, le compilateur n’autorise pas une référence non const lvalue à lier à une variable temporaire.

## <a name="syntax"></a>Syntaxe

> **/Zc:referenceBinding**[**-**]

## <a name="remarks"></a>Notes

Si **/Zc:referenceBinding** est spécifié, le compilateur suit la section 8.5.3 de la norme C ++ 11 et n’autorise pas les expressions qui lient un type défini par l’utilisateur temporaire vers une référence non const lvalue. Par défaut, ou si **/Zc:referenceBinding-** est spécifié, le compilateur autorise ces expressions comme une extension Microsoft, mais un avertissement de niveau 4. Pour la sécurité du code, la portabilité et de la conformité, nous vous recommandons d’utiliser **/Zc:referenceBinding**.

Le **/Zc:referenceBinding** option est désactivée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option du compilateur définit implicitement cette option, mais elle peut être substituée à l’aide de **/Zc:referenceBinding-**.

## <a name="example"></a>Exemple

Cet exemple montre l’extension Microsoft qui permet à une valeur temporaire d’un type défini par l’utilisateur être lié à une référence non const lvalue.

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zc:referenceBinding** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>

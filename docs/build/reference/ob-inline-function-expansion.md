---
title: /Ob (Expansion des fonctions Inline)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 7eb3db1e359349eaf5125a6c8a46a3ac7d847f2f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915483"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Expansion des fonctions Inline)

Contrôle l'expansion inline des fonctions. Par défaut, lors de l’optimisation, l’expansion se produit à la discrétion du compilateur sur toutes les fonctions, souvent appelées *auto-inline*.

## <a name="syntax"></a>Syntaxe

::: moniker range=">=vs-2019"

> **/Ob** {**0**|12|**3**}|

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob** {**0**|12|}

::: moniker-end

## <a name="arguments"></a>Arguments

**entre**\
Valeur par défaut sous [/OD](od-disable-debug.md). Désactive les expansions inline.

**1**\
Autorise l’expansion uniquement des fonctions marquées [inline](../../cpp/inline-functions-cpp.md), [__ inline](../../cpp/inline-functions-cpp.md) ou [__ forceinline](../../cpp/inline-functions-cpp.md), ou dans une fonction membre définie dans une déclaration de classe.

**2**\
La valeur par défaut sous [/O1](o1-o2-minimize-size-maximize-speed.md) et [/O2](o1-o2-minimize-size-maximize-speed.md). Permet au compilateur de développer n’importe quelle fonction qui n’est pas explicitement marquée pour aucune incorporation.

::: moniker range=">=vs-2019"

**3**\
Cette option spécifie une incorporation plus agressive que **/OB2**, mais elle a les mêmes restrictions. L’option **/Ob3** est disponible à partir de Visual Studio 2019.

::: moniker-end

## <a name="remarks"></a>Notes

Le compilateur traite les options d'expansion inline et les mots clés comme des suggestions. Il n’y a aucune garantie que toutes les fonctions seront développées Inline. Vous pouvez désactiver les expansions Inline, mais vous ne pouvez pas forcer le compilateur à incorporer une fonction particulière, même `__forceinline` si vous utilisez le mot clé.

Pour exclure des fonctions en tant que candidats pour l’expansion Inline, vous pouvez utiliser [_ _ declspec (noinline)](../../cpp/noinline.md)ou une région marquée par [#pragma auto_inline (off)](../../preprocessor/auto-inline.md) et [#pragma directives auto_inline (on)](../../preprocessor/auto-inline.md) . Pour plus d’informations sur une autre façon de fournir des indicateurs d’incorporation au compilateur, consultez la [#pragma directive intrinsèque](../../preprocessor/intrinsic.md) .

> [!NOTE]
> Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui seraient autrement en vigueur parce que vous avez spécifié **/ob**, **/OS**ou **/OT**. Pour plus d’informations, consultez [Optimisations guidées par profil](../profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés** > de > configuration**C/C++** **optimisation** .

1. Modifiez la propriété **expansion des fonctions inline** .

::: moniker range=">=vs-2019"

L’option **/Ob3** n’est pas disponible dans la propriété **expansion des fonctions inline** . Pour définir **/Ob3**:

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés** > de > configuration **C/C++**  **ligne de commande** .

1. Entrez **/Ob3** dans **options supplémentaires**.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le code), options](o-options-optimize-code.md)\
[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

---
title: -Ob (Expansion des fonctions Inline) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6755025ff07d79b7e6086fc8c8a59a3bdebdb777
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725255"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Expansion des fonctions Inline)

Contrôle l'expansion inline des fonctions.

## <a name="syntax"></a>Syntaxe

> /OB {0 | 1 | 2}

## <a name="arguments"></a>Arguments

**0**<br/>
Désactive les expansions inline. Par défaut, expansion se produit à la discrétion du compilateur sur toutes les fonctions, souvent appelé *auto-inlining*.

**1**<br/>
Autorise uniquement l’expansion de fonctions marquées [inline](../../cpp/inline-functions-cpp.md), `__inline`, ou `__forceinline`, ou dans une fonction de membre C++ définie dans une déclaration de classe.

**2**<br/>
Valeur par défaut. Autorise l'expansion des fonctions marquées comme `inline`, `__inline`, ou `__forceinline`, et toute autre fonction choisie par le compilateur.

**/ Ob2** est appliqué lorsque [/O1, / O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) ou [/Ox (activer plus optimisations de vitesse)](../../build/reference/ox-full-optimization.md) est utilisé.

Cette option nécessite que vous activiez des optimisations à l’aide de **/O1**, **/O2**, **/Ox**, ou **/Og**.

## <a name="remarks"></a>Notes

Le compilateur traite les options d'expansion inline et les mots clés comme des suggestions. Il n'existe aucune garantie que toutes les fonctions seront développées inline. Vous pouvez désactiver les expansions inline, mais vous ne pouvez pas forcer le compilateur à insérer une fonction particulière, même si vous utilisez le mot clé `__forceinline`.

Vous pouvez utiliser la `#pragma` [auto_inline](../../preprocessor/auto-inline.md) directive pour exclure les fonctions de prendre en compte comme des candidats pour l’expansion inline. Consultez également le `#pragma` [intrinsèque](../../preprocessor/intrinsic.md) directive.

> [!NOTE]
> Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui seraient en vigueur si vous spécifiez **/Ob**, **/Os**, ou **/Ot**. Pour plus d’informations, consultez [optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez **propriétés de Configuration**, **C/C++**, puis sélectionnez **optimisation**.

1. Modifier le **Expansion des fonctions Inline** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le Code), options](../../build/reference/o-options-optimize-code.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
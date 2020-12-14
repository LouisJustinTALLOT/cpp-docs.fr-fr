---
description: En savoir plus sur:/Oy (omission du pointeur de frame)
title: /Oy (Omission du pointeur frame)
ms.date: 11/19/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: dc0f9272bce5ad36840eac9ccdfc7e2465f7e3c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226296"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Omission du pointeur frame)

Empêche la création des pointeurs de frame sur la pile des appels.

## <a name="syntax"></a>Syntaxe

> /Oy [-]

## <a name="remarks"></a>Notes

Cette option accélère les appels de fonction, dans la mesure où aucun pointeur de frame n'a besoin d'être installé, puis supprimé. Il libère également un registre supplémentaire pour une utilisation générale.

**/Oy** active l’omission du pointeur de frame et **/Oy-** désactive l’omission. Dans les compilateurs x64, **/Oy** et **/Oy-** ne sont pas disponibles.

Si votre code requiert un adressage basé sur des frames, vous pouvez spécifier l’option **/Oy-** après l’option **/Ox** ou utiliser [optimize](../../preprocessor/optimize.md) avec les arguments «**y**» et **off** pour obtenir une optimisation maximale avec l’adressage basé sur des trames. Le compilateur détecte la plupart des situations où l’adressage basé sur des trames est requis (par exemple, avec les `_alloca` `setjmp` fonctions et et avec la gestion structurée des exceptions).

Les options [/Ox (activer la plupart des optimisations de vitesse)](ox-full-optimization.md) et [/O1,/O2 (réduire la taille, augmenter la vitesse)](o1-o2-minimize-size-maximize-speed.md) impliquent **/Oy**. La spécification de **/Oy-** après l’option **/Ox**, **/O1** ou **/O2** désactive **/Oy**, qu’il soit explicite ou implicite.

L’option du compilateur **/Oy** rend l’utilisation du débogueur plus difficile, car le compilateur supprime les informations du pointeur de frame. Si vous spécifiez une option de compilateur de débogage ([/Z7,/Zi,/Zi](z7-zi-zi-debug-information-format.md)), nous vous recommandons de spécifier l’option **/Oy-** après toute autre option d’optimisation du compilateur.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés optimisation des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **omettre les pointeurs de frame** . Cette propriété ajoute ou supprime uniquement l’option **/Oy** . Si vous souhaitez ajouter l’option **/Oy-** , sélectionnez la page de propriétés **ligne de commande** et modifiez les **options supplémentaires**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le code), options](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>

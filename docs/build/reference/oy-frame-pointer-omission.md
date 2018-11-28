---
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
ms.openlocfilehash: 343b0e026c2932e97d4a8d4472ba2035d6302661
ms.sourcegitcommit: 3da2cb3ec85e77ddfd4d2a55edb133d580ce4f18
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52330388"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Omission du pointeur frame)

Empêche la création des pointeurs de frame sur la pile des appels.

## <a name="syntax"></a>Syntaxe

> /Oy [-]

## <a name="remarks"></a>Notes

Cette option accélère les appels de fonction, dans la mesure où aucun pointeur de frame n'a besoin d'être installé, puis supprimé. Elle libère également un Registre supplémentaire pour une utilisation générale.

**/Oy** Active l’omission du pointeur de frame et **/Oy-** désactive l’omission. Dans x64 compilateurs, **/Oy** et **/Oy-** ne sont pas disponibles.

Si votre code requiert un adressage basé sur le frame, vous pouvez spécifier le **/Oy-** option après la **/Ox** option ou utilisez [optimiser](../../preprocessor/optimize.md) avec le «**y**» et **hors** arguments pour obtenir une optimisation maximale avec l’adressage en fonction du frame. Le compilateur détecte la plupart des situations où l’adressage en fonction du frame est requis (par exemple, avec le `_alloca` et `setjmp` fonctions et la gestion structurée des exceptions).

Le [/Ox (activer plus optimisations de vitesse)](../../build/reference/ox-full-optimization.md) et [/O1, / O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) options impliquent **/Oy**. Spécification **/Oy-** après le **/Ox**, **/O1**, ou **/O2** option désactive **/Oy**, qu’il s’agisse explicite ou implicite.

Le **/Oy** du compilateur option rend l’utilisation du débogueur plus difficile, car le compilateur supprime les informations de pointeur de frame. Si vous spécifiez une option du compilateur de débogage ([/Z7, / Zi, / Zi](../../build/reference/z7-zi-zi-debug-information-format.md)), nous vous recommandons de spécifier le **/Oy-** option après les autres options de compilateur d’optimisation.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **optimisation** page de propriétés.

1. Modifier le **omission des pointeurs de Frame** propriété. Cette propriété ajoute ou supprime uniquement le **/Oy** option. Si vous souhaitez ajouter le **/Oy-** option, sélectionnez le **ligne de commande** propriété page et modifier **des options supplémentaires**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](../../build/reference/o-options-optimize-code.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>

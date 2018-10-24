---
title: -Oy (Omission du pointeur Frame) | Microsoft Docs
ms.custom: ''
ms.date: 09/22/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
dev_langs:
- C++
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c077b5a350d7381adc5412ca4a318713d720ad6
ms.sourcegitcommit: 1870c342d44b10990fd015e60856225c3026e8c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2018
ms.locfileid: "49963049"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Omission du pointeur frame)

Empêche la création des pointeurs de frame sur la pile des appels.

## <a name="syntax"></a>Syntaxe

> /Oy [-]

## <a name="remarks"></a>Notes

Cette option accélère les appels de fonction, dans la mesure où aucun pointeur de frame n'a besoin d'être installé, puis supprimé. Elle libère également un Registre supplémentaire pour une utilisation générale.

**/Oy** Active l’omission du pointeur de frame et **/Oy-** désactive l’omission. **/Oy** est uniquement disponible dans x86 compilateurs.

Si votre code requiert l’adressage EBP, vous pouvez spécifier le **/Oy-** option après la **/Ox** option ou utilisez [optimiser](../../preprocessor/optimize.md) avec le «**y**» et **hors** arguments pour obtenir une optimisation maximale avec l’adressage EBP. Le compilateur détecte la plupart des situations où l'adressage EBP est requis (par exemple, avec les fonctions `_alloca` et `setjmp`, ainsi qu'avec la gestion des exceptions structurées).

Le [/Ox (activer plus optimisations de vitesse)](../../build/reference/ox-full-optimization.md) et [/O1, / O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) options impliquent **/Oy**. Spécification **/Oy-** après le **/Ox**, **/O1**, ou **/O2** option désactive **/Oy**, qu’il s’agisse explicite ou implicite.

Le **/Oy** du compilateur option rend l’utilisation du débogueur plus difficile, car le compilateur supprime les informations de pointeur de frame. Si vous spécifiez une option du compilateur de débogage ([/Z7, / Zi, / Zi](../../build/reference/z7-zi-zi-debug-information-format.md)), nous vous recommandons de spécifier le **/Oy-** option après les autres options de compilateur d’optimisation.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **optimisation** page de propriétés.

1. Modifier le **omission des pointeurs de Frame** propriété. Cette propriété ajoute ou supprime uniquement le **/Oy** option. Si vous souhaitez ajouter le **/Oy-** , cliquez sur l’option **ligne de commande** et modifier **des options supplémentaires**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](../../build/reference/o-options-optimize-code.md)

[Options du compilateur](../../build/reference/compiler-options.md)

[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)

---
title: -Oy (Omission du pointeur Frame) | Documents Microsoft
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
ms.openlocfilehash: b6feb682d364c4c40fd01e4aff33404c4506d9c1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377259"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Omission du pointeur frame)

Empêche la création des pointeurs de frame sur la pile des appels.

## <a name="syntax"></a>Syntaxe

> /Oy [-]

## <a name="remarks"></a>Notes

Cette option accélère les appels de fonction, dans la mesure où aucun pointeur de frame n'a besoin d'être installé, puis supprimé. Elle libère également un registre supplémentaire (EBP sur l'architecture Intel 386 ou version ultérieure) pour le stockage des variables et sous-expressions fréquemment utilisées.

**/Oy** Active l’omission du pointeur frame et **/Oy-** désactive l’omission. **/Oy** est disponible uniquement dans x86 compilateurs.

Si votre code requiert l’adressage EBP, vous pouvez spécifier le **/Oy-** option après la **/Ox** option ou utilisez [optimiser](../../preprocessor/optimize.md) avec le «**y**» et **hors** arguments pour obtenir une optimisation maximale avec l’adressage EBP. Le compilateur détecte la plupart des situations où l'adressage EBP est requis (par exemple, avec les fonctions `_alloca` et `setjmp`, ainsi qu'avec la gestion des exceptions structurées).

Le [/Ox (activer plus vitesse optimisations)](../../build/reference/ox-full-optimization.md) et [/O1, / O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) options impliquent **/Oy**. Spécification de **/Oy-** après le **/Ox**, **/O1**, ou **/O2** option désactive **/Oy**, qu’il s’agisse explicite ou implicite.

Le **/Oy** option du compilateur fait de l’utilisation du débogueur plus difficile, car le compilateur supprime les informations de pointeur de frame. Si vous spécifiez une option du compilateur de débogage ([/Z7, / Zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), nous vous recommandons de spécifier le **/Oy-** option après toutes les autres options du compilateur d’optimisation.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **optimisation** page de propriétés.

1. Modifier la **omission des pointeurs de Frame** propriété. Cette propriété ajoute ou supprime uniquement le **/Oy** option. Si vous souhaitez ajouter le **/Oy-** , cliquez sur **ligne de commande** et modifier **des options supplémentaires**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](../../build/reference/o-options-optimize-code.md)

[Options du compilateur](../../build/reference/compiler-options.md)

[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
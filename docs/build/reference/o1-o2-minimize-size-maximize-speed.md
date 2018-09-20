---
title: -O1, - O2 (réduire la taille, augmenter la vitesse) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /o2
- /o1
dev_langs:
- C++
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24e57be50c2138cb9e772f6e6a2527300c9296ea
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446476"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Réduire la taille, augmenter la vitesse)

Sélectionne un ensemble prédéfini d’options qui affectent la taille et la vitesse du code généré.

## <a name="syntax"></a>Syntaxe

> / / O2 O1

## <a name="remarks"></a>Notes

Le **/O1** et **/O2** options du compilateur constituent un moyen rapide pour définir plusieurs options d’optimisation spécifiques à la fois. Le **/O1** option définit les options d’optimisation qui créent le code plus petit dans la plupart des cas. Le **/O2** option définit les options qui créent le code le plus rapide dans la plupart des cas. Le **/O2** option est la valeur par défaut pour les versions release. Ce tableau montre les options spécifiques qui sont définies par **/O1** et **/O2**:

|Option|Équivalent à|
|------------|-------------------|
|**/ O1** (réduire la taille)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md)  [ /Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (augmenter la vitesse)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md)  [ /Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** et **/O2** s’excluent mutuellement.

> [!NOTE]
> **x86 spécifique** ces options impliquent l’utilisation de l’Omission du pointeur Frame ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) option.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sous **propriétés de Configuration**, ouvrez **C/C++** , puis choisissez le **optimisation** page de propriétés.

1. Modifier le **optimisation** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](../../build/reference/o-options-optimize-code.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/EH (Modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md)

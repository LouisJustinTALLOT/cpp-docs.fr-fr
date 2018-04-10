---
title: -O1, - O2 (réduire la taille, augmenter la vitesse) | Documents Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f880b3cb806efa63299bf6cfa4aab4c72df23817
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Réduire la taille, augmenter la vitesse)

Sélectionne un ensemble prédéfini d’options qui affectent la taille et la vitesse du code généré.

## <a name="syntax"></a>Syntaxe

> /O1  
> /O2

## <a name="remarks"></a>Notes

Le **/O1** et **/O2** options du compilateur sont un moyen rapide de définir plusieurs options d’optimisation spécifiques à la fois. Le **/O1** option définit les options de l’optimisation individuels qui créent le code plus petit dans la majorité des cas. Le **/O2** option définit les options qui créent le code le plus rapide dans la majorité des cas. Le **/O2** option est la valeur par défaut pour les versions release. Ce tableau montre les options spécifiques qui sont définies par **/O1** et **/O2**:

|Option|Équivalent à|
|------------|-------------------|
|**/ O1** (réduire la taille)|[/Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/Gs](../../build/reference/gs-control-stack-checking-calls.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md)  [ /Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (augmenter la vitesse)|[/Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/Gs](../../build/reference/gs-control-stack-checking-calls.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md)  [ /Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** et **/O2** s’excluent mutuellement.

> [!NOTE]  
> **x86 spécifiques**  
> Ces options impliquent l’utilisation de l’Omission du pointeur Frame ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) option.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sous **propriétés de Configuration**, ouvrez **C/C++** , puis choisissez le **optimisation** page de propriétés.

1. Modifier la **optimisation** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le Code), options](../../build/reference/o-options-optimize-code.md)  
[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
[/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md)
---
title: /O1, /O2 (Réduire la taille, augmenter la vitesse)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
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
ms.openlocfilehash: d33fe6bceae09267fd3f79ffe3dc26864e87c764
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320355"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Réduire la taille, augmenter la vitesse)

Sélectionne un ensemble prédéfini d’options qui affectent la taille et la vitesse du code généré.

## <a name="syntax"></a>Syntaxe

> /O1 /O2

## <a name="remarks"></a>Notes

Le **/O1** et **/O2** options du compilateur constituent un moyen rapide pour définir plusieurs options d’optimisation spécifiques à la fois. Le **/O1** option définit les options d’optimisation qui créent le code plus petit dans la plupart des cas. Le **/O2** option définit les options qui créent le code le plus rapide dans la plupart des cas. Le **/O2** option est la valeur par défaut pour les versions release. Ce tableau montre les options spécifiques qui sont définies par **/O1** et **/O2**:

|Option|Équivalent à|
|------------|-------------------|
|**/ O1** (réduire la taille)|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md)  [ /Gy](gy-enable-function-level-linking.md)|
|**/ O2** (augmenter la vitesse)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/Ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md)  [ /Gy](gy-enable-function-level-linking.md)|

**/ O1** et **/O2** s’excluent mutuellement.

> [!NOTE]
> **x86 spécifique** ces options impliquent l’utilisation de l’Omission du pointeur Frame ([/Oy](oy-frame-pointer-omission.md)) option.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sous **propriétés de Configuration**, ouvrez **C/C++** , puis choisissez le **optimisation** page de propriétés.

1. Modifier le **optimisation** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Modèle de gestion des exceptions)](eh-exception-handling-model.md)

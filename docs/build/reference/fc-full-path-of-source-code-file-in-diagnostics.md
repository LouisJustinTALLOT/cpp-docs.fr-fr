---
description: En savoir plus sur:/FC (chemin d’accès complet du fichier de code source dans les Diagnostics)
title: /FC (Chemin d’accès complet du fichier de code source dans les diagnostics)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 01d1148a32179a7c605a19dc7f2856b7697ae6fb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200674"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Chemin d’accès complet du fichier de code source dans les diagnostics)

Fait en sorte que le compilateur affiche le chemin d’accès complet des fichiers de code source passés au compilateur dans les Diagnostics.

## <a name="syntax"></a>Syntaxe

> /FC

## <a name="remarks"></a>Notes

Prenons l’exemple de code suivant :

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

Sans **/FC**, le texte de diagnostic ressemble à ce texte de diagnostic :

- compiler_option_FC. cpp (5) : erreur C2143 : erreur de syntaxe : absence de « ; » avant « } »

Avec **/FC**, le texte de diagnostic ressemble à ce texte de diagnostic :

- répertoire c:\test\ compiler_option_fc. cpp (5) : erreur C2143 : erreur de syntaxe : '; 'manquant avant'} '

**/FC** est également nécessaire si vous souhaitez afficher le chemin d’accès complet d’un nom de fichier lors de l’utilisation du fichier &#95;&#95;&#95;&#95; macro. Pour plus d’informations sur les&#95;&#95; de fichiers &#95;&#95;, consultez [macros prédéfinies](../../preprocessor/predefined-macros.md) .

L’option **/FC** est impliquée par **/Zi**. Pour plus d’informations sur **/Zi**, consultez [/Z7,/Zi,/ZI (format des informations de débogage)](z7-zi-zi-debug-information-format.md).

**/FC** génère des chemins d’accès complets en minuscules.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **utiliser des chemins d’accès complets** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)

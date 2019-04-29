---
title: /FC (Chemin d’accès complet du fichier de code source dans les diagnostics)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
ms.openlocfilehash: 190174e1e2ac4d160140ddc54f9cc1c3a1b31709
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271292"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Chemin d’accès complet du fichier de code source dans les diagnostics)

Indique au compilateur afficher le chemin d’accès complet des fichiers de code source passés au compilateur dans les diagnostics.

## <a name="syntax"></a>Syntaxe

> /FC

## <a name="remarks"></a>Notes

Prenez l’exemple de code suivant :

```cpp
// compiler_option_FC.cpp
int main( ) {
   int i   // C2143
}
```

Sans **/FC**, le texte de diagnostic devrait être semblable à ce texte de diagnostic :

- compiler_option_FC.cpp (5) : erreur C2143 : erreur de syntaxe : manquant ';' avant '}'

Avec **/FC**, le texte de diagnostic devrait être semblable à ce texte de diagnostic :

- c:\test\compiler_option_FC.cpp(5) : erreur C2143 : erreur de syntaxe : manquant ';' avant '}'

**/FC** est également nécessaire si vous souhaitez afficher le chemin d’accès complet d’un nom de fichier lorsque vous utilisez le &#95; &#95;fichier&#95; &#95; (macro). Consultez [Macros prédéfinies](../../preprocessor/predefined-macros.md) pour plus d’informations sur &#95; &#95;fichier&#95;&#95;.

Le **/FC** option est impliquée par **/Zi**. Pour plus d’informations sur **/Zi**, consultez [/Z7, / Zi, /ZI (Format des informations de débogage)](z7-zi-zi-debug-information-format.md).

**/FC** génère des chemins d’accès complets en minuscules.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **avancé** page de propriétés.

1. Modifier le **utilisation des chemins d’accès complets** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

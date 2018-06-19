---
title: -FC (chemin d’accès complet du fichier de Code Source dans les Diagnostics) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UseFullPaths
- /FC
dev_langs:
- C++
helpviewer_keywords:
- /FC compiler option [C++]
- -FC compiler option [C++]
ms.assetid: 1f11414e-cb42-421b-be68-9d369aab036b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4a721b6887b6c5c07d96a79b06f05e6d7855250b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373203"
---
# <a name="fc-full-path-of-source-code-file-in-diagnostics"></a>/FC (Chemin d’accès complet du fichier de code source dans les diagnostics)

Indique au compilateur afficher le chemin d’accès complet des fichiers de code source passé au compilateur dans le diagnostic.

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

Sans **/FC**, le texte de diagnostic devrait être semblable à ce texte de diagnostic :

- compiler_option_FC.cpp (5) : erreur C2143 : erreur de syntaxe : manquant ';' avant '}'

Avec **/FC**, le texte de diagnostic devrait être semblable à ce texte de diagnostic :

- c:\test\compiler_option_FC.cpp(5) : erreur C2143 : erreur de syntaxe : manquant ';' avant '}'

 **/FC** est également nécessaire si vous souhaitez afficher le chemin d’accès complet d’un nom de fichier lorsque vous utilisez la &#95; &#95;fichier&#95; &#95; (macro). Consultez [Macros prédéfinies](../../preprocessor/predefined-macros.md) pour plus d’informations sur &#95; &#95;fichier&#95;&#95;.

Le **/FC** option est implicite **/Zi**. Pour plus d’informations sur **/Zi**, consultez [/Z7, / Zi, /ZI (Format des informations de débogage)](../../build/reference/z7-zi-zi-debug-information-format.md).

**/FC** génère des chemins d’accès complets en minuscules.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **avancé** page de propriétés.

1. Modifier la **utilisez les chemins d’accès complet** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UseFullPaths%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)

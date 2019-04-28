---
title: /Zo (Améliorer le débogage optimisé)
ms.date: 11/04/2016
f1_keywords:
- -Zo
- /Zo
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
ms.openlocfilehash: 2fb64b0cc39d5b7ff0c96d3eae47197c455526f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315350"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (Améliorer le débogage optimisé)

Génère des informations de débogage avancées pour le code optimisé dans des builds autres que debug.

## <a name="syntax"></a>Syntaxe

```cpp
/Zo[-]
```

## <a name="remarks"></a>Notes

Le **/zo** commutateur de compilateur génère des informations de débogage avancées pour le code optimisé. L'optimisation peut utiliser des registres pour les variables locales, réorganiser le code, vectoriser les boucles et placer les appels de fonction inline. Ces optimisations peuvent rendre moins visible la relation entre le code source et le code objet compilé. Le **/zo** commutateur indique au compilateur de générer des informations de débogage supplémentaires pour les variables locales et les fonctions inline. Utilisez-le pour voir les variables dans le **automatique**, **variables locales**, et **espion** windows lorsque vous parcourez le code optimisé dans le débogueur Visual Studio. Il permet également aux traces de pile d'afficher les fonctions inline dans le débogueur WinDBG. Builds Debug pour lesquelles les optimisations sont désactivées ([/Od](od-disable-debug.md)) n’est pas nécessaire des informations de débogage supplémentaires générées lorsque **/zo** est spécifié. Utilisez le **/zo** commutateur pour déboguer les configurations Release avec l’optimisation activée. Pour plus d’informations sur les commutateurs d’optimisation, consultez [/O Options (Optimize Code)](o-options-optimize-code.md). Le **/Zo** est activée par défaut dans Visual Studio lorsque vous spécifiez des informations de débogage avec **/Zi** ou **/Z7**. Spécifiez **/Zo-** pour désactiver explicitement cette option du compilateur.

Le **/Zo** commutateur n’est disponible à partir de Visual Studio 2013 Update 3, et il remplace le précédemment non documentés **/d2Zi+** basculer.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /Zo dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration**, **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure `/Zo` , puis **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](o-options-optimize-code.md)<br/>
[/Z7, /Zi, /ZI (Format des informations de débogage)](z7-zi-zi-debug-information-format.md)<br/>
[Modifier & Continuer](/visualstudio/debugger/edit-and-continue)

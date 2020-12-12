---
description: En savoir plus sur:/zo (améliorer le débogage optimisé)
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
ms.openlocfilehash: b2d5fb37205a6cf58492d7e6bc9080867ebacf54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224346"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (Améliorer le débogage optimisé)

Génère des informations de débogage avancées pour le code optimisé dans des builds autres que debug.

## <a name="syntax"></a>Syntaxe

```cpp
/Zo[-]
```

## <a name="remarks"></a>Notes

Le commutateur du compilateur **/zo** génère des informations de débogage avancées pour le code optimisé. L'optimisation peut utiliser des registres pour les variables locales, réorganiser le code, vectoriser les boucles et placer les appels de fonction inline. Ces optimisations peuvent rendre moins visible la relation entre le code source et le code objet compilé. Le commutateur **/zo** indique au compilateur de générer des informations de débogage supplémentaires pour les variables locales et les fonctions inline. Utilisez-le pour afficher les variables dans les fenêtres **automatique**, **variables locales** et **espions** lorsque vous parcourez le code optimisé dans le débogueur Visual Studio. Il permet également aux traces de pile d'afficher les fonctions inline dans le débogueur WinDBG. Les versions Debug qui ont des optimisations désactivées ([/OD](od-disable-debug.md)) n’ont pas besoin des informations de débogage supplémentaires générées lorsque **/zo** est spécifié. Utilisez le commutateur **/zo** pour déboguer les configurations Release avec l’optimisation activée. Pour plus d’informations sur les commutateurs d’optimisation, consultez [options/o (optimiser le code)](o-options-optimize-code.md). L’option **/zo** est activée par défaut dans Visual Studio lorsque vous spécifiez des informations de débogage avec **/Zi** ou **/Z7**. Spécifiez **/zo-** pour désactiver explicitement cette option de compilateur.

Le commutateur **/zo** est disponible à partir de Visual Studio 2013 Update 3 et il remplace le commutateur **/d2Zi +** non documenté précédemment.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Pour définir l'option de compilateur /Zo dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **Propriétés de configuration**, **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Modifiez la propriété **options supplémentaires** pour inclure `/Zo` , puis cliquez sur **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/O (optimiser le code), options](o-options-optimize-code.md)<br/>
[/Z7,/Zi,/ZI (format des informations de débogage)](z7-zi-zi-debug-information-format.md)<br/>
[Modifier &amp; Continuer](/visualstudio/debugger/edit-and-continue)

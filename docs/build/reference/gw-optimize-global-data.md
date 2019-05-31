---
title: /Gw (optimiser les données globales)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 8afdb21defbbc8309b27749ab18a40f9555139e5
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450134"
---
# <a name="gw-optimize-global-data"></a>/Gw (optimiser les données globales)

Données globales du package dans les sections COMDAT pour l’optimisation.

## <a name="syntax"></a>Syntaxe

```
/Gw[-]
```

## <a name="remarks"></a>Notes

Le **/Gw** option indique au compilateur de données globales du package dans les sections COMDAT individuelles. Par défaut, **/Gw** est désactivé et doit être explicitement activée. Pour désactiver explicitement, utilisez **/Gw-** . Lorsque les deux **/Gw** et [/GL](gl-whole-program-optimization.md) sont activée, l’éditeur de liens utilise optimisation de la totalité du programme pour comparer des sections COMDAT dans plusieurs fichiers d’objet pour exclure les données globales non référencées ou à fusionner en lecture seule global des données identiques. Cela peut réduire considérablement la taille de la sortie binaire exécutable.

Lorsque vous compilez et liez séparément, vous pouvez utiliser la [/OPT : REF](opt-optimizations.md) option de l’éditeur de liens à exclure de l’exécutable que les données globales non référencées dans des fichiers objets compilées avec la **/Gw** option.

Vous pouvez également utiliser le [/OPT : ICF](opt-optimizations.md) et [/LTCG](ltcg-link-time-code-generation.md) les options de l’éditeur de liens entre eux à fusionner dans le fichier exécutable compilées de tout en lecture seule global des données identiques dans plusieurs fichiers de l’objet avec le **/Gw** option.

Pour plus d’informations, consultez [présentation /Gw commutateur de compilateur](https://devblogs.microsoft.com/cppblog/introducing-gw-compiler-switch/) sur le C++ Blog de l’équipe.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Gw** , puis **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

---
title: /Gw (optimiser les données globales)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: d2c7d8d9a3b3bb877fcf7f4418f3ed20a90a9a11
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420126"
---
# <a name="gw-optimize-global-data"></a>/Gw (optimiser les données globales)

Données globales du package dans les sections COMDAT pour l’optimisation.

## <a name="syntax"></a>Syntaxe

```
/Gw[-]
```

## <a name="remarks"></a>Notes

Le **/Gw** option indique au compilateur de données globales du package dans les sections COMDAT individuelles. Par défaut, **/Gw** est désactivé et doit être explicitement activée. Pour désactiver explicitement, utilisez **/Gw-**. Lorsque les deux **/Gw** et [/GL](../../build/reference/gl-whole-program-optimization.md) sont activée, l’éditeur de liens utilise optimisation de la totalité du programme pour comparer des sections COMDAT dans plusieurs fichiers d’objet pour exclure les données globales non référencées ou à fusionner en lecture seule global des données identiques. Cela peut réduire considérablement la taille de la sortie binaire exécutable.

Lorsque vous compilez et liez séparément, vous pouvez utiliser la [/OPT : REF](../../build/reference/opt-optimizations.md) option de l’éditeur de liens à exclure de l’exécutable que les données globales non référencées dans des fichiers objets compilées avec la **/Gw** option.

Vous pouvez également utiliser le [/OPT : ICF](../../build/reference/opt-optimizations.md) et [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) les options de l’éditeur de liens entre eux à fusionner dans le fichier exécutable compilées de tout en lecture seule global des données identiques dans plusieurs fichiers de l’objet avec le **/Gw** option.

Pour plus d’informations, consultez [présentation /Gw commutateur de compilateur](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) sur le Blog d’équipe Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Gw** , puis **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)

---
title: /GF (Supprimer les doublons)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: 2f2bec446fcec522857b4c05a34311e6c26c9b75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270886"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Supprimer les doublons)

Permet au compilateur de créer une copie unique de chaînes identiques dans l’image de programme et en mémoire pendant l’exécution. Il s’agit d’une optimisation appelée *le regroupement des chaînes* peut créer des programmes plus petits.

## <a name="syntax"></a>Syntaxe

```
/GF
```

## <a name="remarks"></a>Notes

Si vous utilisez **/GF**, le système d’exploitation n’échange pas la partie de la chaîne de la mémoire et peut relire les chaînes à partir du fichier image.

**/GF** regroupe les chaînes en lecture seule. Si vous essayez de modifier les chaînes sous **/GF**, une erreur d’application se produit.

Regroupement des chaînes permet ce qui était censé plusieurs pointeurs vers les tampons de plusieurs pointeurs multiples à une seule mémoire tampon. Dans le code suivant, `s` et `t` sont initialisés avec la même chaîne. Le regroupement des chaînes provoque les faire pointer vers la même mémoire :

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  Le [/Zi](z7-zi-zi-debug-information-format.md) option, utilisée pour modifier & Continuer, définit automatiquement le **/GF** option.

> [!NOTE]
>  Le **/GF** option du compilateur crée une section adressable pour chaque chaîne unique. Et par défaut, un fichier objet peut contenir jusqu'à 65 536 sections adressables. Si votre programme contient plus de 65 536 chaînes, utilisez la [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) option du compilateur pour créer plus de sections.

**/GF** est appliqué lorsque [/O1](o1-o2-minimize-size-maximize-speed.md) ou **/O2** est utilisé.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **génération de Code** page de propriétés.

1. Modifier le **activer le regroupement des chaînes** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

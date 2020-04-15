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
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320491"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Supprimer les doublons)

Permet au compilateur de créer une seule copie de chaînes identiques dans l’image du programme et en mémoire pendant l’exécution. Il s’agit d’une optimisation appelée *mise en commun des chaînes* qui peut créer des programmes plus petits.

## <a name="syntax"></a>Syntaxe

```
/GF
```

## <a name="remarks"></a>Notes

Si vous utilisez **/GF**, le système d’exploitation n’échange pas la partie chaîne de mémoire et peut lire les chaînes à partir du fichier d’image.

**/GF** piscines cordes comme lecture-seulement. Si vous essayez de modifier les chaînes sous **/GF**, une erreur d’application se produit.

La mise en commun des chaînes permet à ce qui était prévu comme des pointeurs multiples pour plusieurs tampons d’être plusieurs pointeurs à un seul tampon. Dans le code `s` `t` suivant, et sont parascés avec la même chaîne. La mise en commun des cordes les amène à indiquer la même mémoire :

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> [L’option /ZI,](z7-zi-zi-debug-information-format.md) utilisée pour Edit and Continue, définit automatiquement l’option **/GF.**

> [!NOTE]
> **L’option compilateur /GF** crée une section adressable pour chaque chaîne unique. Et par défaut, un fichier d’objets peut contenir jusqu’à 65 536 sections adressables. Si votre programme contient plus de 65 536 chaînes, utilisez l’option de compilateur [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) pour créer plus de sections.

**/GF** est en vigueur lorsque [/O1](o1-o2-minimize-size-maximize-speed.md) ou [/O2](o1-o2-minimize-size-maximize-speed.md) est utilisé.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriété **Code Generation.**

1. Modifier la propriété **Enable String Pooling.**

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

---
description: En savoir plus sur:/GF (éliminer les chaînes dupliquées)
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
ms.openlocfilehash: 65c8cca610b9e01cf49939c2074a698b00c6e338
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191938"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Supprimer les doublons)

Permet au compilateur de créer une copie unique de chaînes identiques dans l’image de programme et en mémoire pendant l’exécution. Il s’agit d’une optimisation appelée *regroupement de chaînes* qui peut créer des programmes plus petits.

## <a name="syntax"></a>Syntaxe

```
/GF
```

## <a name="remarks"></a>Notes

Si vous utilisez **/GF**, le système d’exploitation n’échange pas la partie de la mémoire de la chaîne et peut lire les chaînes à partir du fichier image.

**/GF** regroupe les chaînes en lecture seule. Si vous essayez de modifier des chaînes sous **/GF**, une erreur d’application se produit.

Le regroupement de chaînes permet de faire de ce qui était prévu comme plusieurs pointeurs vers plusieurs mémoires tampons plusieurs pointeurs vers une seule mémoire tampon. Dans le code suivant, `s` et `t` sont initialisés avec la même chaîne. Le regroupement de chaînes fait pointer vers la même mémoire :

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> L’option [/Zi](z7-zi-zi-debug-information-format.md) , utilisée pour modifier & continuer, définit automatiquement l’option **/GF** .

> [!NOTE]
> L’option du compilateur **/GF** crée une section adressable pour chaque chaîne unique. Par défaut, un fichier objet peut contenir jusqu’à 65 536 sections adressables. Si votre programme contient plus de 65 536 chaînes, utilisez l’option du compilateur [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) pour créer d’autres sections.

**/GF** est activé lorsque [/O1](o1-o2-minimize-size-maximize-speed.md) ou [/O2](o1-o2-minimize-size-maximize-speed.md) est utilisé.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **génération de code** .

1. Modifiez la propriété **activer le regroupement de chaînes** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)

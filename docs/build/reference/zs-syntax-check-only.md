---
description: En savoir plus sur:/ZS (vérification de la syntaxe uniquement)
title: /Zs (Contrôler la syntaxe uniquement)
ms.date: 11/04/2016
f1_keywords:
- /zs
helpviewer_keywords:
- -Zs compiler option [C++]
- Syntax Check Only compiler option
- Zs compiler option
- /Zs compiler option [C++]
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
ms.openlocfilehash: a4f5e2227104003a637db1d921fd959ea0a11ad7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224294"
---
# <a name="zs-syntax-check-only"></a>/Zs (Contrôler la syntaxe uniquement)

Indique au compilateur de vérifier uniquement la syntaxe des fichiers sources sur la ligne de commande.

## <a name="syntax"></a>Syntaxe

```
/Zs
```

## <a name="remarks"></a>Notes

Lorsque cette option est utilisée, aucun fichier de sortie n’est créé et les messages d’erreur sont écrits dans la sortie standard.

L’option **/ZS** offre un moyen rapide de rechercher et de corriger les erreurs de syntaxe avant la compilation et la liaison d’un fichier source.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)

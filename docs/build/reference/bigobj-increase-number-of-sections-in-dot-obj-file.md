---
description: En savoir plus sur:/bigobj (augmenter le nombre de sections dans. Fichier OBJ)
title: /bigobj (Augmenter le nombre de sections dans le fichier .obj)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 4e820211ec46ad2a2d125552f95fb8a82c6f57ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182695"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Augmenter le nombre de sections dans le fichier .obj)

**/bigobj** augmente le nombre de sections qu’un fichier objet peut contenir.

## <a name="syntax"></a>Syntaxe

> **/bigobj**

## <a name="remarks"></a>Notes

Par défaut, un fichier objet peut contenir jusqu’à 65 279 (presque 2 ^ 16) sections adressables. Cette limite s’applique quelle que soit la plateforme cible spécifiée. **/bigobj** augmente la capacité de l’adresse à 4 294 967 296 (2 ^ 32).

La plupart des modules ne génèrent jamais de fichier. obj contenant plus de 65 279 sections. Toutefois, le code généré par l’ordinateur, ou le code qui utilise intensivement des bibliothèques de modèles, peut nécessiter des fichiers. obj qui peuvent contenir plus de sections. **/bigobj** est activé par défaut sur les projets plateforme Windows universelle (UWP), car le code XAML généré par l’ordinateur comprend un grand nombre d’en-têtes. Si vous désactivez cette option sur un projet d’application UWP, votre code risque de générer une erreur de compilateur C1128.

Pour plus d’informations sur le format de fichier d’objet PE-COFF, consultez [format PE](/windows/win32/debug/pe-format) dans la documentation de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Entrez l’option du compilateur **/bigobj** dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)

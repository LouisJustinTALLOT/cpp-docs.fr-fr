---
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: 57aece79dfab617121371e0489aa80f18e143372
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57819688"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Nécessite des instructions de déplacement entier pour les valeurs à virgule flottante et désactive certaines optimisations à virgule flottante de charge.

## <a name="syntax"></a>Syntaxe

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Notes

**/ Qsafe_fp_loads** est uniquement disponible dans les compilateurs qui ciblent x86 ; il n’est pas disponible dans les compilateurs qui ciblent x64 ou ARM.

**/ Qsafe_fp_loads** force le compilateur à utiliser des instructions de déplacement entier au lieu d’obtenir des instructions à virgule flottante de déplacement pour déplacer des données entre la mémoire et MMX inscrit. Cette option désactive également les optimisations du chargement s’inscrire pour les valeurs à virgule flottante qui peut être chargé dans plusieurs chemins d’accès de contrôle lorsque la valeur peut provoquer une exception lors du chargement, par exemple, une valeur NaN.

Cette option est remplacée par [/fp : sauf](fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** spécifie un sous-ensemble du comportement du compilateur qui est spécifié par **/fp : sauf**.

**/ Qsafe_fp_loads** est incompatible avec [/CLR](clr-common-language-runtime-compilation.md) et [Fast](fp-specify-floating-point-behavior.md). Pour plus d’informations sur les options de compilateur point flottant, consultez [/fp (spécifier le comportement de virgule flottante)](fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** pour appliquer la modification.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)

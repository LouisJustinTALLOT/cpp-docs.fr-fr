---
description: En savoir plus sur les éléments suivants:/Qsafe_fp_loads
title: /Qsafe_fp_loads
ms.date: 01/24/2018
ms.openlocfilehash: e569b308d2da982c72775699ff2149daa45a8f2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225516"
---
# <a name="qsafe_fp_loads"></a>/Qsafe_fp_loads

Requiert des instructions de déplacement d’entiers pour les valeurs à virgule flottante et désactive certaines optimisations de charge à virgule flottante.

## <a name="syntax"></a>Syntaxe

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Notes

**/Qsafe_fp_loads** est uniquement disponible dans les compilateurs qui ciblent x86 ; elle n’est pas disponible dans les compilateurs qui ciblent x64 ou ARM.

**/Qsafe_fp_loads** force le compilateur à utiliser des instructions de déplacement d’entiers au lieu d’instructions de déplacement à virgule flottante pour déplacer des données entre la mémoire et les registres MMX. Cette option désactive également enregistrer l’optimisation de chargement pour les valeurs à virgule flottante qui peuvent être chargées dans plusieurs chemins de contrôle lorsque la valeur peut provoquer une exception lors du chargement, par exemple une valeur NaN.

Cette option est remplacée par [/FP : except](fp-specify-floating-point-behavior.md). **/Qsafe_fp_loads** spécifie un sous-ensemble du comportement du compilateur spécifié par **/FP : except**.

**/Qsafe_fp_loads** est incompatible avec [/CLR](clr-common-language-runtime-compilation.md) et [/FP : Fast](fp-specify-floating-point-behavior.md). Pour plus d’informations sur les options du compilateur à virgule flottante, consultez [/FP (spécifier le comportement de Floating-Point)](fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** . Choisissez **OK** pour appliquer le changement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)

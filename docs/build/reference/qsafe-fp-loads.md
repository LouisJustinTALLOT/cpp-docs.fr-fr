---
title: / Qsafe_fp_loads | Microsoft Docs
ms.custom: ''
ms.date: 01/24/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af28b391390f28be4e111b55c909dcae66ca2f8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713659"
---
# <a name="qsafefploads"></a>/Qsafe_fp_loads

Nécessite des instructions de déplacement entier pour les valeurs à virgule flottante et désactive certaines optimisations à virgule flottante de charge.

## <a name="syntax"></a>Syntaxe

> **/Qsafe_fp_loads**

## <a name="remarks"></a>Notes

**/ Qsafe_fp_loads** est uniquement disponible dans les compilateurs qui ciblent x86 ; il n’est pas disponible dans les compilateurs qui ciblent x64 ou ARM.

**/ Qsafe_fp_loads** force le compilateur à utiliser des instructions de déplacement entier au lieu d’obtenir des instructions à virgule flottante de déplacement pour déplacer des données entre la mémoire et MMX inscrit. Cette option désactive également les optimisations du chargement s’inscrire pour les valeurs à virgule flottante qui peut être chargé dans plusieurs chemins d’accès de contrôle lorsque la valeur peut provoquer une exception lors du chargement, par exemple, une valeur NaN.

Cette option est remplacée par [/fp : sauf](../../build/reference/fp-specify-floating-point-behavior.md). **/ Qsafe_fp_loads** spécifie un sous-ensemble du comportement du compilateur qui est spécifié par **/fp : sauf**.

**/ Qsafe_fp_loads** est incompatible avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) et [Fast](../../build/reference/fp-specify-floating-point-behavior.md). Pour plus d’informations sur les options de compilateur point flottant, consultez [/fp (spécifier le comportement de virgule flottante)](../../build/reference/fp-specify-floating-point-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** pour appliquer la modification.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q (opérations de bas niveau), options](../../build/reference/q-options-low-level-operations.md)
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)

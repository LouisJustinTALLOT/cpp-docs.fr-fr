---
description: En savoir plus sur les éléments suivants:/ALIGN (alignement des sections)
title: /ALIGN (Alignement des sections)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: d8a9af473252a2eff8957c5d2b4c54c7f7c862aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187258"
---
# <a name="align-section-alignment"></a>/ALIGN (Alignement des sections)

## <a name="syntax"></a>Syntaxe

> **/Align**[**:**_Number_]

### <a name="arguments"></a>Arguments

*number*<br/>
Valeur d’alignement en octets.

## <a name="remarks"></a>Notes

L’option **/align** spécifie l’alignement de chaque section dans l’espace d’adressage linéaire du programme. L’argument *Number* est en octets et doit être une puissance de deux. La valeur par défaut est 4 Ko (4096). L’éditeur de liens émet un avertissement si l’alignement produit une image non valide.

À moins que vous écriviez une application telle qu’un pilote de périphérique, vous n’avez pas besoin de modifier l’alignement.

Il est possible de modifier l’alignement d’une section particulière avec le paramètre align avec l’option [/section](section-specify-section-attributes.md) .

La valeur d’alignement que vous spécifiez ne peut pas être inférieure à l’alignement de section le plus grand.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Choisissez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Entrez l’option dans la zone **options supplémentaires** . Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

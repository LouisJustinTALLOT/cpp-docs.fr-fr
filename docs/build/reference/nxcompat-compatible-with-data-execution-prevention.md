---
title: /NXCOMPAT (Compatible avec la prévention de l’exécution de données) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /NXCOMPAT
dev_langs:
- C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52cf47335c1bed55ca38d508789d65902b335f0f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707627"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible avec la prévention de l'exécution des données)

Indique qu’un fichier exécutable est compatible avec la fonctionnalité de prévention de l’exécution des données Windows.

## <a name="syntax"></a>Syntaxe

> **/ NXCOMPAT**[**: NO**]

## <a name="remarks"></a>Notes

Par défaut, **/NXCOMPAT** se trouve sur.

**Sa** peut être utilisé pour spécifier explicitement un fichier exécutable est incompatible avec la prévention de l’exécution des données.

Pour plus d’informations sur la prévention de l’exécution des données, consultez les articles suivants :

- [Une description détaillée de la fonctionnalité de prévention de l’exécution des données (PED)](https://support.microsoft.com/en-us/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Prévention de l’exécution des données](/windows/desktop/Memory/data-execution-prevention)

- [Prévention de l’exécution des données (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Choisissez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)

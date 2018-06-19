---
title: /NXCOMPAT (Compatible avec la prévention de l’exécution des données) | Documents Microsoft
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
ms.openlocfilehash: bb4f8a91545a196bc92fdc0ec44e89a7d5680185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374802"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible avec la prévention de l'exécution des données)

Indique qu’un fichier exécutable est compatible avec la fonctionnalité de prévention de l’exécution des données Windows.

## <a name="syntax"></a>Syntaxe

> **/ NXCOMPAT**[**: NO**]

## <a name="remarks"></a>Notes

Par défaut, **/NXCOMPAT** sur.

**Sa** peut être utilisé pour spécifier explicitement un fichier exécutable comme étant incompatible avec la prévention de l’exécution des données.

Pour plus d’informations sur la prévention de l’exécution des données, consultez les articles suivants :

- [Une description détaillée de la fonctionnalité de prévention de l’exécution des données (PED)](http://go.microsoft.com/fwlink/p/?linkid=157771)

- [Prévention de l’exécution des données](http://go.microsoft.com/fwlink/p/?linkid=157770)

- [Prévention de l’exécution des données (Windows Embedded)](http://go.microsoft.com/fwlink/p/?linkid=157768)

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Choisissez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)  
[Options de l’éditeur de liens](../../build/reference/linker-options.md)  

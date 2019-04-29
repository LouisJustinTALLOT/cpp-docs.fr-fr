---
title: /NXCOMPAT (compatible avec la prévention de l'exécution des données)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: a8550337189f9c92a1c8a8d86f2f9b2b829bbc3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320368"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible avec la prévention de l'exécution des données)

Indique qu’un fichier exécutable est compatible avec la fonctionnalité de prévention de l’exécution des données Windows.

## <a name="syntax"></a>Syntaxe

> **/NXCOMPAT**[**:NO**]

## <a name="remarks"></a>Notes

Par défaut, **/NXCOMPAT** se trouve sur.

**Sa** peut être utilisé pour spécifier explicitement un fichier exécutable est incompatible avec la prévention de l’exécution des données.

Pour plus d’informations sur la prévention de l’exécution des données, consultez les articles suivants :

- [Une description détaillée de la fonctionnalité de prévention de l’exécution des données (PED)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Prévention de l’exécution des données](/windows/desktop/Memory/data-execution-prevention)

- [Prévention de l’exécution des données (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Choisissez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Entrez l’option dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

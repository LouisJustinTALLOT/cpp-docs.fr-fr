---
title: /NXCOMPAT (compatible avec la prévention de l'exécution des données)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 7c788f5ec499f0edf0c44f1ff269af9767af6c08
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492661"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible avec la prévention de l'exécution des données)

Indique qu’un fichier exécutable est compatible avec la fonctionnalité de prévention de l’exécution des données Windows.

## <a name="syntax"></a>Syntaxe

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Notes

Par défaut, **/NXCOMPAT** est activé.

**/NXCOMPAT: no** peut être utilisé pour spécifier explicitement un exécutable comme étant incompatible avec la prévention de l’exécution des données.

Pour plus d’informations sur la prévention de l’exécution des données, consultez les articles suivants:

- [Description détaillée de la fonctionnalité de prévention de l’exécution des données (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Prévention de l’exécution des données](/windows/win32/Memory/data-execution-prevention)

- [Prévention de l’exécution des données (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Choisissez la page de propriétés**ligne de commande** de l'**éditeur de liens** >  **Propriétés** > de configuration.

1. Entrez l’option dans la zone **options supplémentaires** . Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

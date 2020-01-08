---
title: /NXCOMPAT (compatible avec la prévention de l'exécution des données)
description: Décrit l’option de l'C++ éditeur de liens Microsoft C/(MSVC)/NXCOMPAT, qui marque un exécutable comme étant compatible avec la prévention de l’exécution des données (DEP).
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298985"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible avec la prévention de l'exécution des données)

Indique qu’un fichier exécutable est compatible avec la fonctionnalité de prévention de l’exécution des données Windows.

## <a name="syntax"></a>Syntaxe

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Notes

Par défaut, **/NXCOMPAT** est activé.

**/NXCOMPAT : no** peut être utilisé pour spécifier explicitement un exécutable comme étant incompatible avec la prévention de l’exécution des données.

Pour plus d’informations sur la prévention de l’exécution des données, consultez les articles suivants :

- [Prévention de l’exécution des données](/windows/win32/Memory/data-execution-prevention)

- [Prévention de l’exécution des données (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Choisissez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés ligne de **commande** .

1. Entrez l’option dans la zone **options supplémentaires** . Choisissez **OK** ou **appliquer** pour appliquer la modification.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

\ de référence de l' [éditeur de liens MSVC](linking.md)
[Options de l’éditeur de liens MSVC](linker-options.md)

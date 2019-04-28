---
title: /IMPLIB (Nommer la bibliothèque d'importation)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: dc9a9220d55f7831a00f70ec155cc5b57a695818
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269984"
---
# <a name="implib-name-import-library"></a>/IMPLIB (Nommer la bibliothèque d'importation)

> / IMPLIB :*nom de fichier*

## <a name="parameters"></a>Paramètres

*filename*<br/>
Un nom spécifié par l’utilisateur pour la bibliothèque d’importation. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

L’option /IMPLIB substitue le nom par défaut pour la bibliothèque d’importation LINK crée lorsqu’il génère un programme qui contient des exportations. Le nom par défaut est constitué du nom de base du fichier de sortie principal et l’extension. lib. Un programme contient des exportations si un ou plusieurs des éléments suivants sont spécifiés :

- Le [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) mot clé dans le code source

- [EXPORTATIONS](exports.md) instruction dans un fichier .def

- Un [/EXPORT](export-exports-a-function.md) spécification dans une commande LINK

LINK ignore /IMPLIB lorsqu’une bibliothèque d’importation n’est pas créée. Si aucune exportation n’est spécifiées, le lien ne crée pas une bibliothèque d’importation. Si un fichier d’exportation est utilisé dans la build, lien suppose qu’une bibliothèque d’importation existe déjà et qu’il ne crée pas une. Pour plus d’informations sur les bibliothèques d’importation et les fichiers d’exportation, consultez [Référence LIB](lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **bibliothèque d’importation** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

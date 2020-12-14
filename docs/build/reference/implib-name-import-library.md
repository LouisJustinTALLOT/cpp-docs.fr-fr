---
description: En savoir plus sur:/IMPLIB (nommer la bibliothèque d’importation)
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
ms.openlocfilehash: 2a5ea590368d1bc3abbecf38845e97a99a0d1f96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191314"
---
# <a name="implib-name-import-library"></a>/IMPLIB (Nommer la bibliothèque d'importation)

> /IMPLIB :*NomFichier*

## <a name="parameters"></a>Paramètres

*filename*<br/>
Nom spécifié par l’utilisateur pour la bibliothèque d’importation. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

L’option/IMPLIB remplace le nom par défaut de la bibliothèque d’importation créée par LINK lors de la génération d’un programme qui contient des exportations. Le nom par défaut est formé à partir du nom de base du fichier de sortie principal et de l’extension. lib. Un programme contient des exportations Si une ou plusieurs des conditions suivantes sont spécifiées :

- Mot clé [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) dans le code source

- Instruction [exports](exports.md) dans un fichier. def

- Une spécification [/Export](export-exports-a-function.md) dans une commande Link

LINK ignore/IMPLIB quand une bibliothèque d’importation n’est pas en cours de création. Si aucune exportation n’est spécifiée, LINK ne crée pas de bibliothèque d’importation. Si un fichier d’exportation est utilisé dans la build, LINK suppose qu’une bibliothèque d’importation existe déjà et n’en crée pas une. Pour plus d’informations sur les bibliothèques d’importation et les fichiers d’exportation, consultez [référence lib](lib-reference.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **avancé** .

1. Modifiez la propriété **bibliothèque d’importation** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

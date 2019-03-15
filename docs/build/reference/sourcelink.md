---
title: / SOURCELINK (fichier Sourcelink inclure dans le fichier PDB)
ms.date: 08/20/2018
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: 1643727d8f556a905eccbfa9626d1aaa8ea63cbf
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816605"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/ SOURCELINK (fichier inclure un lien de Source dans le fichier PDB)

Spécifie un fichier de configuration de lien de la Source à inclure dans le fichier PDB généré par l’éditeur de liens.

## <a name="syntax"></a>Syntaxe

> **/ SOURCELINK :**_nom de fichier_

## <a name="arguments"></a>Arguments

*filename*<br/>
Spécifie au format JSON fichier de configuration qui contient un mappage simple des chemins d’accès de fichier local à l’URL où le fichier source peut être récupéré pour l’affichage par le débogueur. Pour plus d’informations sur le format de ce fichier, consultez [schéma JSON de lien Source](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Notes

Lien de source est un système indépendant du contrôle de code source et de langue pour fournir le débogage du code source pour les fichiers binaires. Lien de source est pris en charge pour les fichiers binaires de C++ natifs à partir de Visual Studio 2017 version 15.8. Pour une vue d’ensemble de la Source de liaison, consultez [Sourcelink](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Pour plus d’informations sur la façon d’utiliser le lien Source dans vos projets et comment générer le fichier SourceLink dans le cadre de votre projet, consultez [à l’aide de la liaison de Source](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Pour définir l’option de l’éditeur de liens /SOURCELINK dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez **/SOURCELINK :**_filename_ , puis **OK** ou **appliquer**pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Cette option n’a pas un équivalent de programmation.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

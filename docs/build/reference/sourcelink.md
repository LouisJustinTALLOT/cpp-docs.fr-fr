---
title: /SOURCELINK (Inclure le fichier Sourcelink dans PDB)
description: Guide de référence de l’option de liaison /SOURCELINK dans Microsoft C.
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336066"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK (Inclure le fichier Source Link dans PDB)

Spécifie un fichier de configuration Source Link à inclure dans le fichier PDB généré par le linker.

## <a name="syntax"></a>Syntaxe

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>Arguments

*Fichier*<br/>
Spécifie un fichier de configuration formaté JSON qui contient une simple cartographie des trajectoires de fichiers locaux vers les URL pour les fichiers sources à afficher dans le débagé. Pour plus d’informations sur le format de ce fichier, voir [Source Link JSON Schema](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Notes

Source Link est un système agnostique de contrôle de la langue et des sources pour fournir le débogage de source pour les binaires. Source Link est pris en charge pour les binaires natifs de CMD à partir de Visual Studio 2017 version 15.8. Pour un aperçu de Source Link, voir [Source Link](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md). Pour plus d’informations sur la façon d’utiliser Source Link dans vos projets, et comment générer le fichier SourceLink dans le cadre de votre projet, voir [Using Source Link](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Définir l’option de liaison /SOURCELINK dans Visual Studio

1. Ouvrez la boîte de dialogue **des Pages De la propriété** pour le projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page propriété **Configuration Properties** > **Linker** > **Command Line.**

1. Dans la boîte **d’options supplémentaire,** **`/SOURCELINK:`** _`filename`_ ajoutez et choisissez **ensuite OK** ou **appliquez** pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Cette option n’a pas d’équivalent programmatique.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

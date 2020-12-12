---
description: En savoir plus sur:/MAP (générer le mappage)
title: /MAP (Générer fichier de mappage)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
ms.openlocfilehash: 28e3823099b4893dcf344a0b1aae99577d850821
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176429"
---
# <a name="map-generate-mapfile"></a>/MAP (Générer fichier de mappage)

```
/MAP[:filename]
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Nom spécifié par l’utilisateur pour le mappage. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

L’option/MAP indique à l’éditeur de liens de créer un mappage.

Par défaut, l’éditeur de liens nomme le mappage avec le nom de base du programme et l’extension. map. Le nom de fichier facultatif vous permet de remplacer le nom par défaut d’un *fichier* de mappage.

Un fichier de mappage est un fichier texte qui contient les informations suivantes sur le programme lié :

- Nom du module, qui est le nom de base du fichier

- L’horodateur de l’en-tête du fichier programme (pas du système de fichiers)

- Liste de groupes dans le programme, avec l’adresse de début de chaque groupe (comme *section*:*offset*), la longueur, le nom de groupe et la classe

- Liste de symboles publics, avec chaque adresse (comme *section*:*offset*), le nom du symbole, l’adresse plate et le fichier. obj où le symbole est défini

- Point d’entrée ( *section*:*offset*)

L’option [/MapInfo](mapinfo-include-information-in-mapfile.md) spécifie des informations supplémentaires à inclure dans le mappage.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Déboguer** .

1. Modifiez la propriété **générer le fichier de mappage** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Localisez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

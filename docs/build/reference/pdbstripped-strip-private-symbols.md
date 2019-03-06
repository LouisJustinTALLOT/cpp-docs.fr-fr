---
title: /PDBSTRIPPED (Supprimer les symboles privés)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: c0a79eb8d1c00be2b855ec08ffe44f4e7d7a2e05
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412625"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Supprimer les symboles privés)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Un nom spécifié par l’utilisateur pour la base de données du programme supprimée (PDB) qui crée l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option /PDBSTRIPPED crée un deuxième fichier de base de données (PDB) du programme lorsque vous générez votre image de programme avec toute du compilateur ou l’éditeur de liens générant un fichier PDB ([/DEBUG](../../build/reference/debug-generate-debug-info.md), [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), /Zd ou /Zi). Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients. Le second fichier PDB contiendra uniquement :

- Symboles publics

- La liste des fichiers objets et les parties de l’exécutable auquel ils contribuent

- Frame pointeur optimisation (FPO) les enregistrements de débogage utilisés pour parcourir la pile

Le fichier PDB supprimé ne contiendra pas :

- Informations de type

- Informations de numéro de ligne

- Symboles CodeView des fichiers par objet tels que ceux des fonctions, des variables locales et des données statiques

Le fichier PDB complet sera toujours être généré lorsque vous utilisez /PDBSTRIPPED.

Si vous ne créez pas un fichier PDB, /PDBSTRIPPED est ignoré.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modifier le **suppression des symboles privés** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)

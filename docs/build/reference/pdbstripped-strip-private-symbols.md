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
ms.openlocfilehash: 3ed36eca727a15a3c70bc51a07cd3c143d7f66da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320134"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Supprimer les symboles privés)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Un nom spécifié par l’utilisateur pour la base de données du programme supprimée (PDB) qui crée l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option /PDBSTRIPPED crée un deuxième fichier de base de données (PDB) du programme lorsque vous générez votre image de programme avec toute du compilateur ou l’éditeur de liens générant un fichier PDB ([/DEBUG](debug-generate-debug-info.md), [/Z7](z7-zi-zi-debug-information-format.md), /Zd ou /Zi). Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients. Le second fichier PDB contiendra uniquement :

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

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modifier le **suppression des symboles privés** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

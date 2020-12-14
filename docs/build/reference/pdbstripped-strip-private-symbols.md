---
description: En savoir plus sur:/PDBSTRIPPED (supprimer les symboles privés)
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
ms.openlocfilehash: 27e70281ad12f4401ad6557ead9be11a38684472
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226036"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (Supprimer les symboles privés)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Nom spécifié par l’utilisateur pour la base de données du programme (PDB) supprimée créée par l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option/PDBSTRIPPED crée un deuxième fichier de base de données du programme (PDB) lorsque vous générez votre image de programme avec l’une des options du compilateur ou de l’éditeur de liens qui génèrent un fichier PDB ([/Debug](debug-generate-debug-info.md), [/Z7](z7-zi-zi-debug-information-format.md),/Zd ou/Zi). Ce second fichier PDB omet les symboles que vous ne souhaitez pas envoyer à vos clients. Le deuxième fichier PDB contient uniquement les éléments suivants :

- Symboles publics

- Liste des fichiers objets et des parties de l’exécutable auquel ils contribuent

- Enregistrements de débogage FPO (frame pointer Optimization) utilisés pour traverser la pile

Le fichier PDB supprimé ne contient pas les éléments suivants :

- Informations de type

- Informations sur le numéro de ligne

- Symboles CodeView du fichier par objet, tels que ceux pour les fonctions, les variables locales et les données statiques

Le fichier PDB complet est toujours généré quand vous utilisez/PDBSTRIPPED.

Si vous ne créez pas de fichier PDB,/PDBSTRIPPED est ignoré.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Déboguer** .

1. Modifiez la propriété **Supprimer les symboles privés** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

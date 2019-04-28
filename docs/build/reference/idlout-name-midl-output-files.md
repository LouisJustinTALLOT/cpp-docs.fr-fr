---
title: /IDLOUT (Nommer les fichiers de sortie MIDL)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 3816bb85cb3c711075e3fefeec2d706c2f8cc2ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291572"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Nommer les fichiers de sortie MIDL)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Paramètres

*path*<br/>
Une spécification de chemin d’accès absolu ou relatif. En spécifiant un chemin d’accès, vous affectez uniquement l’emplacement d’un fichier .idl ; tous les autres fichiers sont placés dans le répertoire du projet.

*filename*<br/>
Spécifie le nom du fichier .idl créé par le compilateur MIDL. Aucune extension de fichier n’est supposée ; Spécifiez *filename*.idl si vous souhaitez une extension .idl.

## <a name="remarks"></a>Notes

L’option /IDLOUT spécifie le nom et l’extension du fichier .idl.

Le compilateur MIDL est appelé par l’éditeur de liens MSVC lors de la liaison de projets qui ont le [module](../../windows/module-cpp.md) attribut.

L’option /IDLOUT spécifie également les noms de fichiers des autres fichiers de sortie associés au compilateur MIDL :

- *filename*.tlb

- *filename*_p.c

- *nom de fichier*_i.c

- *nom de fichier*.h

*nom de fichier* est le paramètre que vous passez à /IDLOUT. Si [/TLBOUT](tlbout-name-dot-tlb-file.md) est spécifié, le fichier .tlb obtiendra son nom de /TLBOUT *filename*.

Si vous spécifiiez /TLBOUT, l’éditeur de liens crée vc70.tlb, vc70.idl, vc70_p.c, vc70_i.c et vc70.h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **IDL incorporé** page de propriétés.

1. Modifier le **nom de fichier de Base IDL fusionné** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IGNOREIDL (Ne pas traiter les attributs dans MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Spécifier des options de ligne de commande MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Générer un programmes par attributs](../../windows/building-an-attributed-program.md)

---
title: /TLBOUT (Nommer le fichier .TLB)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 3eaf4305c58ca70619e032f80e661b9c768f7813
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425521"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Nommer le fichier .TLB)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Arguments

*path*<br/>
Une spécification de chemin d’accès absolu ou relatif pour où le fichier .tlb doit être créé.

*filename*<br/>
Spécifie le nom du fichier .tlb créé par le compilateur MIDL. Aucune extension de fichier n’est supposée ; Spécifiez *filename*.tlb si vous souhaitez une extension .tlb.

## <a name="remarks"></a>Notes

L’option /TLBOUT Spécifie le nom et l’extension du fichier .tlb.

Le compilateur MIDL est appelé par l’éditeur de liens Visual C++ lors de la liaison de projets qui ont le [module](../../windows/module-cpp.md) attribut.

Si /TLBOUT n’est pas spécifié, le fichier .tlb obtiendra son nom à partir de [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md) *filename*. Si /IDLOUT n’est pas spécifié, le fichier .tlb s’appellera vc70.tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **IDL incorporé** page de propriétés.

1. Modifier le **bibliothèque de types** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)<br/>
[/IGNOREIDL (Ne pas traiter les attributs dans MIDL)](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (Spécifier des options de ligne de commande MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)<br/>
[Générer un programmes par attributs](../../windows/building-an-attributed-program.md)

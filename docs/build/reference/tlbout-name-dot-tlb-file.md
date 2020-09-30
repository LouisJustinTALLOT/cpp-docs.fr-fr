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
ms.openlocfilehash: 62913eaadd0f0a88f05ce347a6778062a1e66f17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509332"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (Nommer le fichier .TLB)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>Arguments

*path*<br/>
Spécification de chemin d’accès absolu ou relatif pour l’emplacement où le fichier. tlb doit être créé.

*extension*<br/>
Spécifie le nom du fichier. tlb créé par le compilateur MIDL. Aucune extension de fichier n’est utilisée. Spécifiez *filename*. tlb si vous souhaitez une extension. tlb.

## <a name="remarks"></a>Remarques

L’option/TLBOUT spécifie le nom et l’extension du fichier. tlb.

Le compilateur MIDL est appelé par l’éditeur de liens MSVC lors de la liaison de projets qui ont l’attribut [module](../../windows/attributes/module-cpp.md) .

Si/TLBOUT n’est pas spécifié, le fichier. tlb obtiendra son nom à partir du *nom*de fichier [/Idlout](idlout-name-midl-output-files.md) . Si/IDLOUT n’est pas spécifié, le fichier. tlb sera appelé vc70. tlb.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **IDL incorporé** .

1. Modifiez la propriété de la **bibliothèque de types** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IGNOREIDL (ne pas traiter les attributs dans MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (spécifier les options de ligne de commande MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Générer un programmes par attributs](../../windows/attributes/cpp-attributes-com-net.md)

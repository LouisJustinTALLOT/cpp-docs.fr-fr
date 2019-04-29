---
title: /IGNOREIDL (Don&#39;t traiter les attributs dans MIDL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: 210778adecd87ffdd5f2702c10106f12bd5a1b79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291676"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t traiter les attributs dans MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Notes

L’option /IGNOREIDL spécifie que toute [attributs IDL](../../windows/idl-attributes.md) de source de code ne doit pas être traité dans un fichier .idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **IDL incorporé** page de propriétés.

1. Modifier le **IDL incorporé** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IDLOUT (Nommer les fichiers de sortie MIDL)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (Nommer le fichier .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (Spécifier des options de ligne de commande MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Générer un programmes par attributs](../../windows/building-an-attributed-program.md)

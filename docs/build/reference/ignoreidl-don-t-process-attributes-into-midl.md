---
title: -IGNOREIDL (Don&#39;t traiter les attributs dans MIDL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
dev_langs:
- C++
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7014440c3479016c89b774f9a80cc03fc4b5d4c3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708225"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t traiter les attributs dans MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Notes

L’option /IGNOREIDL spécifie que toute [attributs IDL](../../windows/idl-attributes.md) de source de code ne doit pas être traité dans un fichier .idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **IDL incorporé** page de propriétés.

1. Modifier le **IDL incorporé** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)<br/>
[/IDLOUT (nommer les fichiers de sortie MIDL)](../../build/reference/idlout-name-midl-output-files.md)
[/TLBOUT (nom. Fichier TLB)](../../build/reference/tlbout-name-dot-tlb-file.md)
[/MIDL (spécifier les Options de ligne de commande MIDL)](../../build/reference/midl-specify-midl-command-line-options.md)
[générer un programmes par attributs](../../windows/building-an-attributed-program.md)
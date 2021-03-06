---
description: En savoir plus sur:/IGNOREIDL (Don&#39;t traiter les attributs dans MIDL)
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
ms.openlocfilehash: c68b3ec2f9bd5607ef523667bcddc68b22d3c34c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199816"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/IGNOREIDL (Don&#39;t traiter les attributs dans MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Notes

L’option/IGNOREIDL spécifie que les [attributs IDL](../../windows/attributes/idl-attributes.md) du code source ne doivent pas être traités dans un fichier. idl.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **IDL incorporé** .

1. Modifiez la propriété **IDL incorporé ignoré** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IDLOUT (nommer les fichiers de sortie MIDL)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (nom. Fichier TLB)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (spécifier les options de ligne de commande MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Générer un programmes par attributs](../../windows/attributes/cpp-attributes-com-net.md)

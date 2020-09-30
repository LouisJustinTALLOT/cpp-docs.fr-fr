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
ms.openlocfilehash: 8dc26a0564a979c918d1eb1eb85e63e9c73caba0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506934"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (Nommer les fichiers de sortie MIDL)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>Paramètres

*path*<br/>
Spécification de chemin d’accès absolu ou relatif. En spécifiant un chemin d’accès, vous affectez uniquement l’emplacement d’un fichier. idl ; tous les autres fichiers sont placés dans le répertoire du projet.

*extension*<br/>
Spécifie le nom du fichier. idl créé par le compilateur MIDL. Aucune extension de fichier n’est utilisée. Spécifiez *filename*. idl si vous souhaitez une extension. idl.

## <a name="remarks"></a>Remarques

L’option/IDLOUT spécifie le nom et l’extension du fichier. idl.

Le compilateur MIDL est appelé par l’éditeur de liens MSVC lors de la liaison de projets qui ont l’attribut [module](../../windows/attributes/module-cpp.md) .

/IDLOUT spécifie également les noms de fichiers des autres fichiers de sortie associés au compilateur MIDL :

- *filename*. tlb

- *nom de fichier*_p. c

- *nom de fichier*_i. c

- *nom de fichier*. h

*filename* est le paramètre que vous transmettez à/Idlout. Si [/TLBOUT](tlbout-name-dot-tlb-file.md) est spécifié, le fichier. tlb obtiendra son nom à partir du *nom*de fichier/TLBOUT.

Si vous ne spécifiez ni/IDLOUT ni/TLBOUT, l’éditeur de liens crée vc70. tlb, vc70. idl, vc70_p. c, vc70_i. c et vc70. h.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **IDL incorporé** .

1. Modifiez la propriété **nom de fichier de base IDL de fusion** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)<br/>
[/IGNOREIDL (ne pas traiter les attributs dans MIDL)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (spécifier les options de ligne de commande MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Générer un programmes par attributs](../../windows/attributes/cpp-attributes-com-net.md)

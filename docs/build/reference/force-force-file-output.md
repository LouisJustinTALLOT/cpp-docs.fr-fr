---
title: /FORCE (Forcer la sortie d'un fichier)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: 28b1c21382832c8775ffe0406038a482e74076c5
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299721"
---
# <a name="force-force-file-output"></a>/FORCE (Forcer la sortie d'un fichier)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Notes

L’option/FORCE indique à l’éditeur de liens de créer un fichier. exe ou une DLL valide même si un symbole est référencé mais pas défini ou s’il est multiplié par plusieurs.

L’option/FORCE peut accepter un argument facultatif:

- Utilisez/FORCE: MULTIPLE pour créer un fichier de sortie, qu’il s’agisse d’une liaison ou pas de plusieurs définitions pour un symbole.

- Utilisez/FORCE: Unresolved pour créer un fichier de sortie, que LINK trouve ou non un symbole non défini. /FORCE: Unresolved est ignoré si le symbole de point d’entrée n’est pas résolu.

/FORCE sans argument implique à la fois plusieurs et non résolus.

Un fichier créé avec cette option peut ne pas s’exécuter comme prévu. L’éditeur de liens ne lie pas de façon incrémentielle lorsque l’option/FORCE est spécifiée.

Si un module est compilé avec **/CLR**, **/force** ne crée pas d’image.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet et choisissez **Propriétés**. 

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans la zone **options supplémentaires** .

Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

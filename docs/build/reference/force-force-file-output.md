---
title: /FORCE (Forcer la sortie d'un fichier)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: af7962a4b3b5805e7e0c4d59752254c8ade17f7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292469"
---
# <a name="force-force-file-output"></a>/FORCE (Forcer la sortie d'un fichier)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Notes

L’option /FORCE indique à l’éditeur de liens pour créer un fichier .exe valide ou DLL même si un symbole est référencé, mais pas défini ou est défini plusieurs fois.

L’option peut prendre un argument facultatif :

- Utilisez multiple pour créer un fichier de sortie si LINK trouve plusieurs définitions pour un symbole ou non.

- Option/force : UNRESOLVED crée un fichier de sortie si LINK trouve un symbole non défini ou non. / FORCE : non RÉSOLUE est ignoré si le symbole de point d’entrée n’est pas résolu.

/FORCE sans argument implique les deux plusieurs et non résolus.

Un fichier créé avec cette option peut ne pas fonctionner comme prévu. L’éditeur de liens n’est pas lier par incrément lorsque l’option/force est spécifiée.

Si un module est compilé avec **/CLR**, **/FORCE** ne crée pas une image.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

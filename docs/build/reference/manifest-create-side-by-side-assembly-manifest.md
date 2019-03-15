---
title: /MANIFEST (Créer un manifeste d'assembly côte à côte)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateManifest
helpviewer_keywords:
- -MANIFEST linker option
- /MANIFEST linker option
- MANIFEST linker option
ms.assetid: 98c52e1e-712c-4f49-b149-4d0a3501b600
ms.openlocfilehash: 9a3ca3980a9cdff4e67885b2ad47ffa2385b0774
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807817"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Créer un manifeste d'assembly côte à côte)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>Notes

/ MANIFESTE spécifie que l’éditeur de liens doit créer un fichier manifeste côte à côte. Pour plus d’informations sur les fichiers manifeste, consultez [référence des fichiers manifeste](/windows/desktop/SbsCs/manifest-files-reference).

La valeur par défaut est /MANIFEST.

Le /MANIFEST : incorporer option spécifie que l’éditeur de liens doit incorporer le fichier manifeste dans l’image en tant que ressource de type RT_MANIFEST. Le paramètre facultatif `ID` paramètre est l’ID de ressource à utiliser pour le manifeste. Utilisez la valeur 1 pour un fichier exécutable. Utilisez la valeur 2 pour une DLL pour lui permettre de spécifier les dépendances privés. Si le `ID` paramètre n’est pas spécifié, la valeur par défaut est 2 si l’option /DLL est définie ; sinon, la valeur par défaut est 1.

À compter de Visual Studio 2008, les fichiers manifeste pour les fichiers exécutables contiennent une section qui spécifie les informations de contrôle de compte utilisateur (UAC). Si vous spécifiez /MANIFEST mais que vous ne spécifiez ni [/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md) ni [/DLL](dll-build-a-dll.md), un fragment du contrôle par défaut qui a la valeur de niveau de contrôle de compte utilisateur *asInvoker* est inséré dans le manifeste. Pour plus d’informations sur les niveaux UAC, consultez [/MANIFESTUAC (informations UAC incorpore dans le manifeste)](manifestuac-embeds-uac-information-in-manifest.md).

Pour modifier le comportement par défaut pour le compte d’utilisateur, effectuez l’une d'entre elles :

- Spécifiez l’option/MANIFESTUAC et définissez le niveau de l’UAC sur la valeur souhaitée.

- Ou spécifiez l’option : no si vous ne souhaitez pas générer un fragment du contrôle dans le manifeste.

Si vous ne spécifiez pas /MANIFEST, mais spécifiez [/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) des commentaires, un fichier manifest est créé. Un fichier manifest n’est pas créé si vous spécifiez/manifest : no.

Si vous spécifiez /MANIFEST, le nom du fichier manifeste est la même que le nom de votre fichier de sortie, mais avec l’extension .manifest ajoutée au nom de fichier. Par exemple, si votre nom de fichier de sortie est MyFile.exe, le nom du fichier manifeste est MyFile.exe.manifest.  Si vous spécifiez MANIFESTFILE :*nom*, le nom du manifeste est ce que vous spécifiez dans *nom*.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **le fichier manifeste** page de propriétés.

1. Modifier le **génération d’un manifeste** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

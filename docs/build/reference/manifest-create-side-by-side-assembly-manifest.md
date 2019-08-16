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
ms.openlocfilehash: ea58b43accdd854665fad3b70d7aecbc9eaa0f9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492778"
---
# <a name="manifest-create-side-by-side-assembly-manifest"></a>/MANIFEST (Créer un manifeste d'assembly côte à côte)

```
/MANIFEST[:{EMBED[,ID=#]|NO}]
```

## <a name="remarks"></a>Notes

/MANIFEST spécifie que l’éditeur de liens doit créer un fichier manifeste côte à côte. Pour plus d’informations sur les fichiers manifestes, consultez [référence des fichiers manifestes](/windows/win32/SbsCs/manifest-files-reference).

La valeur par défaut est/MANIFEST.

L’option/MANIFEST: EMBED spécifie que l’éditeur de liens doit incorporer le fichier manifeste dans l’image en tant que ressource de type RT_MANIFEST. Le paramètre `ID` facultatif est l’ID de ressource à utiliser pour le manifeste. Utilisez la valeur 1 pour un fichier exécutable. Utilisez la valeur 2 pour une DLL pour lui permettre de spécifier des dépendances privées. Si le `ID` paramètre n’est pas spécifié, la valeur par défaut est 2 si l’option/dll est définie; sinon, la valeur par défaut est 1.

À compter de Visual Studio 2008, les fichiers manifeste pour les exécutables contiennent une section qui spécifie les informations de contrôle de compte d’utilisateur (UAC). Si vous spécifiez/MANIFEST mais que vous ne spécifiez ni [/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md) ni [/dll](dll-build-a-dll.md), un fragment UAC par défaut dont le niveau UAC est défini sur asInvoker est inséré dans le manifeste. Pour plus d’informations sur les niveaux de contrôle de compte d’utilisateur, consultez [/MANIFESTUAC (incorpore les informations UAC dans le manifeste)](manifestuac-embeds-uac-information-in-manifest.md).

Pour modifier le comportement par défaut pour le contrôle de compte d’utilisateur, effectuez l’une des opérations suivantes:

- Spécifiez l’option/MANIFESTUAC et définissez le niveau UAC sur la valeur souhaitée.

- Ou spécifiez l’option/MANIFESTUAC: NO si vous ne souhaitez pas générer un fragment UAC dans le manifeste.

Si vous ne spécifiez pas/MANIFEST mais que vous spécifiez des commentaires [/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) , un fichier manifeste est créé. Un fichier manifeste n’est pas créé si vous spécifiez/MANIFEST: NO.

Si vous spécifiez/MANIFEST, le nom du fichier manifeste est le même que celui de votre fichier de sortie, mais avec l’extension. manifest ajoutée au nom de fichier. Par exemple, si le nom de votre fichier de sortie est MyFile. exe, le nom du fichier manifeste est MyFile. exe. manifest.  Si vous spécifiez/MANIFESTFILE:*Name*, le nom du manifeste est celui que vous spécifiez dans *Name*.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **Éditeur de liens**.

1. Sélectionnez la page de propriétés **fichier manifeste** .

1. Modifiez la propriété **générer le manifeste** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateManifest%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

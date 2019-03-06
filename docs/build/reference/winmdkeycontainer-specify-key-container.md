---
title: /WINMDKEYCONTAINER (spécifier un conteneur de clé de nom fort)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 5424b928f80bf73aedb731f835b72d20bfd0c4a2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416590"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (spécifier un conteneur de clé de nom fort)

Spécifie un conteneur de clé pour signer un fichier de métadonnées Windows (.winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Notes

Ressemble à la [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) option de l’éditeur de liens qui est appliquée à un fichier (.winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **conteneur de clé de métadonnées Windows** , entrez l’emplacement.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)

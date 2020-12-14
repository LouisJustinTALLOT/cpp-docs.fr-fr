---
description: En savoir plus sur:/WINMDKEYCONTAINER (spécifier un conteneur de clé)
title: /WINMDKEYCONTAINER (spécifier un conteneur de clé de nom fort)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 94b203c56b7724c2b2569ba22039da38c4501985
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258991"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (spécifier un conteneur de clé de nom fort)

Spécifie un conteneur de clé pour signer un fichier de métadonnées Windows (. winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Notes

Ressemble à l’option de l’éditeur de liens [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md) appliquée à un fichier (. winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **métadonnées Windows** .

1. Dans la zone **conteneur de clé de métadonnées Windows** , entrez l’emplacement.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

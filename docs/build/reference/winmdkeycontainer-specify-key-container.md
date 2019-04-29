---
title: /WINMDKEYCONTAINER (spécifier un conteneur de clé de nom fort)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 0b6cb42fc391d94634ae90e5a4cc17e69a14ff09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316513"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (spécifier un conteneur de clé de nom fort)

Spécifie un conteneur de clé pour signer un fichier de métadonnées Windows (.winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Notes

Ressemble à la [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md) option de l’éditeur de liens qui est appliquée à un fichier (.winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **conteneur de clé de métadonnées Windows** , entrez l’emplacement.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

---
title: /WINMDKEYFILE (spécifier un fichier de clé)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 4b0c847bc5be6c73b78af4aa15b0074c712cc840
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820401"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (spécifier un fichier de clé)

Spécifie une clé ou une paire de clés pour signer un fichier de métadonnées du Runtime Windows (.winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Notes

Ressemble à la [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) option de l’éditeur de liens qui est appliquée à un fichier .winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **fichier de clé de métadonnées Windows** , entrez l’emplacement du fichier.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

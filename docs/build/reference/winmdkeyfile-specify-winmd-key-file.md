---
description: En savoir plus sur:/WINMDKEYFILE (spécifier le fichier de clé winmd)
title: /WINMDKEYFILE (spécifier un fichier de clé)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 0e7b23de62613f51c3824b107e55180bb54780d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258900"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (spécifier un fichier de clé)

Spécifie une clé ou une paire de clés pour signer un fichier de métadonnées de Windows Runtime (. winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Notes

Ressemble à l’option de l’éditeur de liens [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) qui est appliquée à un fichier. winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **métadonnées Windows** .

1. Dans la zone **fichier de clé de métadonnées Windows** , entrez l’emplacement du fichier.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

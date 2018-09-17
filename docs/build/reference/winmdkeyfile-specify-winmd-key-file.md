---
title: -WINMDKEYFILE (spécifier un fichier de clé) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
dev_langs:
- C++
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d688db3039681fc684e6344e4a27ae7a64544757
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714441"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (spécifier un fichier de clé)

Spécifie une clé ou une paire de clés pour signer un fichier de métadonnées du Runtime Windows (.winmd).

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Notes

Ressemble à la [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) option de l’éditeur de liens qui est appliquée à un fichier .winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **fichier de clé de métadonnées Windows** , entrez l’emplacement du fichier.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
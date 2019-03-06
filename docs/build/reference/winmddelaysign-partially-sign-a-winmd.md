---
title: /WINMDDELAYSIGN (signer partiellement un winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 85698362a753e147a28922db19b456d4d649e55d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421457"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (signer partiellement un winmd)

Permet la signature partielle d’un fichier de métadonnées du Runtime Windows (.winmd) en plaçant la clé publique dans le fichier.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Notes

Ressemble à la [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) option de l’éditeur de liens est appliquée au fichier .winmd. Utilisez **/WINMDDELAYSIGN** si vous souhaitez placer uniquement la clé publique dans le fichier .winmd. Par défaut, l’éditeur de liens se comporte comme si **/winmddelaysign : no** ont été spécifiées ; autrement dit, elle ne déconnecte pas le fichier winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **Windows métadonnées** page de propriétés.

1. Dans le **temporiser la signature de métadonnées Windows** liste déroulante, sélectionnez l’option souhaitée.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)

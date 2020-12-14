---
description: En savoir plus sur:/WINMDDELAYSIGN (signer partiellement un winmd)
title: /WINMDDELAYSIGN (signer partiellement un winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 801b172f52a9beb9d09617644b3096e460359724
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259056"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (signer partiellement un winmd)

Active la signature partielle d’un fichier de métadonnées de Windows Runtime (. winmd) en plaçant la clé publique dans le fichier.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Notes

Ressemble à l’option d’éditeur de liens [/delaysign](delaysign-partially-sign-an-assembly.md) qui est appliquée au fichier. winmd. Utilisez **/WINMDDELAYSIGN** si vous souhaitez placer uniquement la clé publique dans le fichier. winmd. Par défaut, l’éditeur de liens agit comme si **/WINMDDELAYSIGN : no** était spécifié ; autrement dit, il ne signe pas le fichier winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **métadonnées Windows** .

1. Dans la zone de liste déroulante **temporisation des métadonnées Windows** , sélectionnez l’option souhaitée.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

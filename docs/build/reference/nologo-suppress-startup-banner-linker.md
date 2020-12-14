---
description: En savoir plus sur:/NOLOGO (supprimer la bannière de démarrage) (éditeur de liens)
title: /NOLOGO (Suppression de la bannière de démarrage) (Éditeur de liens)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: 48edea691e254f0754d29ab5ea4d8055221c4b69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196553"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Suppression de la bannière de démarrage) (Éditeur de liens)

```
/NOLOGO
```

## <a name="remarks"></a>Notes

L’option/NOLOGO empêche l’affichage du message de copyright et du numéro de version.

Cette option supprime également l’écho des fichiers de commandes. Pour plus d’informations, consultez [lier des fichiers de commandes](linking.md).

Par défaut, ces informations sont envoyées par l’éditeur de liens à la fenêtre sortie. Sur la ligne de commande, elle est envoyée à la sortie standard et peut être redirigée vers un fichier.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Cette option ne doit être utilisée qu’à partir de la ligne de commande.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Cette option de l’éditeur de liens ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)

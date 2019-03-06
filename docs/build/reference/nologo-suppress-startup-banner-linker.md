---
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
ms.openlocfilehash: 1b966c1f7af556a85aadcafaa8ed43da5b3f75df
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422154"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Suppression de la bannière de démarrage) (Éditeur de liens)

```
/NOLOGO
```

## <a name="remarks"></a>Notes

L’option /NOLOGO empêche l’affichage de l’auteur message et numéro de version.

Cette option supprime également la répercussion des fichiers de commandes. Pour plus d’informations, consultez [fichiers de commandes LINK](../../build/reference/link-command-files.md).

Par défaut, ces informations sont transmises par l’éditeur de liens dans la fenêtre Sortie. Sur la ligne de commande, il est envoyé vers la sortie standard et peut être redirigée vers un fichier.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Cette option doit uniquement être utilisée à partir de la ligne de commande.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Cette option de l’éditeur de liens ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)

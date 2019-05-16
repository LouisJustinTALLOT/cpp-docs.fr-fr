---
title: Noms du contrôle, Assistant Contrôle ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: 17c1b30811fa1d9c3f3bc04a46553c617eff966b
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708145"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Noms du contrôle, Assistant Contrôle ActiveX MFC

Spécifiez les noms de la classe de contrôle et de la classe de page de propriétés, les noms de type et les identificateurs de type pour votre contrôle. À l’exception de **nom court**, tous les autres champs peuvent être modifiés de manière indépendante. Si vous modifiez le texte de **nom court**, la modification est répercutée dans les noms de tous les autres champs de cette page. Ce comportement d’affectation de noms est conçu pour rendre tous les noms facilement identifiable pour vous lorsque vous développez votre contrôle.

- **Nom court**

   Fournir un nom abrégé pour le contrôle. Par défaut, ce nom est basé sur le nom de projet que vous avez fourni dans le **nouveau projet** boîte de dialogue. Le nom que vous fournissez détermine les noms de classes, les noms de types et les identificateurs de type, sauf si vous modifiez ces champs individuellement.

- **Nom de classe de contrôle**

   Par défaut, le nom de la classe de contrôle est basé sur le nom court, avec `C` en tant que préfixe et `Ctrl` comme suffixe. Par exemple, si votre contrôle court de nom est `Price`, le nom de classe de contrôle est `CPriceCtrl`.

- **Fichier .h du contrôle**

   Par défaut, le nom du fichier d’en-tête est basé sur le nom court, avec `Ctrl` en guise de suffixe et `.h` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, le nom de fichier d’en-tête est `PriceCtrl.h`. Le nom dans ce champ doit correspondre au nom de classe de contrôle.

- **Fichier .cpp du contrôle**

   Par défaut, le nom du fichier d’en-tête est basé sur le nom court, avec `Ctrl` en guise de suffixe et `.cpp` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, le nom de fichier d’en-tête est `PriceCtrl.cpp`. Le nom dans ce champ doit correspondre au nom de l’en-tête.

- **Nom de type de contrôle**

   Par défaut, le nom du type de contrôle est basé sur le nom court, suivi par `Control`. Par exemple, si votre contrôle court de nom est `Price`, le nom de type de classe de contrôle est `Price Control`. Si vous modifiez la valeur dans ce champ, assurez-vous que le nom indique un héritage.

- **ID de type de contrôle**

   Définit l’ID de type de contrôle de la classe de contrôle. Le contrôle écrit cette chaîne dans le Registre lorsqu’il est ajouté à un projet. Applications de conteneur utilisent cette chaîne pour créer une instance du contrôle.

   Par défaut, l’ID de type de contrôle est basé sur le nom du projet, que vous avez spécifié dans le **nouveau projet** boîte de dialogue et le nom court. Ce nom doit correspondre au nom de type.

   Par défaut, l’ID de type de contrôle s’affiche comme suit :

   *ProjectName.ShortName*Ctrl.1

   Si vous modifiez le nom court dans cette boîte de dialogue, l’ID de type de contrôle s’affiche comme suit :

   *ProjectName.NewShortName*Ctrl.1

- **Nom de classe de PropPage**

   Par défaut, le nom de la classe de page de propriétés est basé sur le nom court, avec `C` en tant que préfixe et `PropPage` comme suffixe. Par exemple, si votre contrôle court de nom est `Price`, le nom de classe de page de propriétés est `CPricePropPage`. Ce nom doit correspondre au nom de la classe du contrôle, avec `PropPage`.

- **Fichier .h de PropPage**

   Par défaut, le nom du fichier d’en-tête de page propriété repose sur le nom court, avec comme un `PropPage` en guise de suffixe et `.h` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, nom de fichier en-tête de page de propriétés est `PricePropPage.h`. Ce nom doit correspondre au nom de classe.

- **Fichier .cpp de PropPage**

   Par défaut, le nom du fichier d’implémentation de propriété page repose sur le nom court, avec comme un `PropPage` en guise de suffixe et `.cpp` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, nom de fichier en-tête de page de propriétés est `PricePropPage.cpp`. Ce nom doit correspondre le nom de fichier d’en-tête.

- **Nom de type de PropPage**

   Par défaut, le nom de type de page de propriétés est basé sur le nom court, suivi par `Property Page`. Par exemple, si votre contrôle court de nom est `Price`, le nom de type de page de propriétés est `Price Property Page`. Si vous modifiez la valeur dans ce champ, assurez-vous que le nom indique la classe du contrôle.

- **ID du type de PropPage**

   Définit l’ID de la classe de page de propriétés. Le contrôle écrit cette chaîne dans le Registre lorsqu’il est appliqué à un projet. Une application conteneur utilise cette chaîne pour créer une instance de la page de propriétés du contrôle.

   Par défaut, l’ID de type de page de propriétés est basé sur le nom du projet, que vous avez spécifié dans le **nouveau projet** boîte de dialogue et le nom court. Ce nom doit correspondre au nom de type.

   Par défaut, l’ID de type de page de propriété s’affiche comme suit :

   *ProjectName.ShortName*PropPage.1

   Si vous modifiez le nom court dans cette boîte de dialogue, l’ID de type de page de propriété s’affiche comme suit :

   *ProjectName.NewShortName*PropPage.1

## <a name="see-also"></a>Voir aussi

[Contrôle ActiveX MFC, Assistant](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Paramètres de l’application, Assistant Contrôle ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Paramètres du contrôle, Assistant Contrôle ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Types de fichiers créés pour Visual Studio C++ projets](../../build/reference/file-types-created-for-visual-cpp-projects.md)


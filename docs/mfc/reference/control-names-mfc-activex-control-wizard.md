---
description: 'En savoir plus sur : noms de contrôle, Assistant contrôle ActiveX MFC'
title: Noms du contrôle, Assistant Contrôle ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: 26d329465c13c3988a3e9d4d7ccd06294f3b2be3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345236"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Noms du contrôle, Assistant Contrôle ActiveX MFC

Spécifiez les noms de la classe de contrôle et de la classe de page de propriétés, les noms de types et les identificateurs de type pour votre contrôle. À l’exception du **nom abrégé**, tous les autres champs peuvent être modifiés indépendamment. Si vous modifiez le texte pour **Short Name**, la modification est répercutée sur les noms de tous les autres champs de cette page. Ce comportement de nommage est conçu pour rendre tous les noms faciles à identifier lors du développement de votre contrôle.

- **Nom court**

   Fournissez un nom abrégé pour le contrôle. Par défaut, ce nom est basé sur le nom de projet que vous avez fourni dans la boîte de dialogue **nouveau projet** . Le nom que vous fournissez détermine les noms de classe, les noms de types et les identificateurs de type, sauf si vous modifiez ces champs individuellement.

- **Nom de la classe du contrôle**

   Par défaut, le nom de la classe de contrôle est basé sur le nom abrégé, avec `C` comme préfixe et `Ctrl` comme suffixe. Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom de la classe de contrôle est `CPriceCtrl` .

- **Fichier. h du contrôle**

   Par défaut, le nom du fichier d’en-tête est basé sur le nom abrégé, avec `Ctrl` comme suffixe et `.h` comme extension de fichier. Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom du fichier d’en-tête est `PriceCtrl.h` . Le nom de ce champ doit correspondre au nom de la classe de contrôle.

- **Fichier. cpp du contrôle**

   Par défaut, le nom du fichier d’en-tête est basé sur le nom abrégé, avec `Ctrl` comme suffixe et `.cpp` comme extension de fichier. Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom du fichier d’en-tête est `PriceCtrl.cpp` . Le nom de ce champ doit correspondre au nom de l’en-tête.

- **Nom du type de contrôle**

   Par défaut, le nom du type de contrôle est basé sur le nom abrégé, suivi de `Control` . Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom du type de classe du contrôle est `Price Control` . Si vous modifiez la valeur dans ce champ, assurez-vous que le nom indique un héritage.

- **ID du type de contrôle**

   Définit l’ID du type de contrôle de la classe de contrôle. Le contrôle écrit cette chaîne dans le Registre lorsqu’elle est ajoutée à un projet. Les applications de conteneur utilisent cette chaîne pour créer une instance du contrôle.

   Par défaut, l’ID du type de contrôle est basé sur le nom du projet, que vous avez indiqué dans la boîte de dialogue **nouveau projet** et sur le nom abrégé. Ce nom doit correspondre au nom de type.

   Par défaut, l’ID du type de contrôle se présente comme suit :

   *NomProjet. ShortName* Ctrl. 1

   Si vous modifiez le nom abrégé dans cette boîte de dialogue, l’ID du type de contrôle s’affiche comme suit :

   *NomProjet. NewShortName* Ctrl. 1

- **Nom de la classe de PropPage**

   Par défaut, le nom de la classe de la page de propriétés est basé sur le nom abrégé, avec `C` comme préfixe et `PropPage` comme suffixe. Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom de la classe de la page de propriétés est `CPricePropPage` . Ce nom doit correspondre au nom de la classe de contrôle, ajouté à `PropPage` .

- **Fichier. h de PropPage**

   Par défaut, le nom du fichier d’en-tête de la page de propriétés est basé sur le nom abrégé, avec comme `PropPage` suffixe et comme `.h` extension de fichier. Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom du fichier d’en-tête de la page de propriétés est `PricePropPage.h` . Ce nom doit correspondre au nom de la classe.

- **Fichier. cpp de PropPage**

   Par défaut, le nom du fichier d’implémentation de la page de propriétés est basé sur le nom abrégé, avec comme `PropPage` suffixe et comme `.cpp` extension de fichier. Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom du fichier d’en-tête de la page de propriétés est `PricePropPage.cpp` . Ce nom doit correspondre au nom du fichier d’en-tête.

- **Nom du type de PropPage**

   Par défaut, le nom du type de la page de propriétés est basé sur le nom abrégé, suivi de `Property Page` . Par exemple, si le nom abrégé de votre contrôle est `Price` , le nom du type de la page de propriétés est `Price Property Page` . Si vous modifiez la valeur dans ce champ, assurez-vous que le nom indique la classe de contrôle.

- **ID de type de PropPage**

   Définit l’ID de la classe de la page de propriétés. Le contrôle écrit cette chaîne dans le Registre lorsqu’elle est appliquée à un projet. Une application conteneur utilise cette chaîne pour créer une instance de la page de propriétés du contrôle.

   Par défaut, l’ID du type de la page de propriétés est basé sur le nom du projet, que vous avez indiqué dans la boîte de dialogue **nouveau projet** et sur le nom abrégé. Ce nom doit correspondre au nom de type.

   Par défaut, l’ID de type de page de propriétés s’affiche comme suit :

   *NomProjet. ShortName* PropPage. 1

   Si vous modifiez le nom abrégé dans cette boîte de dialogue, l’ID du type de page de propriétés s’affiche comme suit :

   *NomProjet. NewShortName* PropPage. 1

## <a name="see-also"></a>Voir aussi

[Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Paramètres de l’application, Assistant contrôle ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Paramètres du contrôle, Assistant contrôle ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Types de fichiers créés pour les projets Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)

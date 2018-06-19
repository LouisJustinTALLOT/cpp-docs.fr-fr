---
title: Noms du contrôle, Assistant contrôle ActiveX MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.names
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08a406bf633715f6a6e9546295da3b02a41f0063
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369308"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Noms du contrôle, Assistant Contrôle ActiveX MFC
Spécifier les noms de la classe de contrôle et de la classe de page de propriétés, les noms de type et les identificateurs de type pour votre contrôle. À l’exception de **nom court**, tous les autres champs peuvent être modifiés de manière indépendante. Si vous modifiez le texte de **nom court**, la modification est répercutée dans les noms de tous les autres champs de cette page. Ce comportement d’affectation de noms est conçu pour rendre tous les noms de facilement identifiables pour vous lorsque vous développez votre contrôle.  
  
 **Nom court**  
 Fournissez un nom abrégé pour le contrôle. Par défaut, ce nom est basé sur le nom de projet fourni dans le **nouveau projet** boîte de dialogue. Le nom que vous fournissez détermine les noms de classe, les noms de types et les identificateurs de type, sauf si vous modifiez ces champs individuellement.  
  
 **Nom de classe de contrôle**  
 Par défaut, le nom de la classe du contrôle est basé sur le nom court, avec `C` en tant que préfixe et `Ctrl` comme suffixe. Par exemple, si votre contrôle court de nom est `Price`, le nom de classe du contrôle est `CPriceCtrl`.  
  
 **Fichier .h de contrôle**  
 Par défaut, le nom du fichier d’en-tête est basé sur le nom court, avec `Ctrl` comme suffixe et `.h` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, le nom de fichier d’en-tête est `PriceCtrl.h`. Le nom de ce champ doit correspondre au nom de classe de contrôle.  
  
 **Fichier .cpp du contrôle**  
 Par défaut, le nom du fichier d’en-tête est basé sur le nom court, avec `Ctrl` comme suffixe et `.cpp` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, le nom de fichier d’en-tête est `PriceCtrl.cpp`. Le nom de ce champ doit correspondre au nom de l’en-tête.  
  
 **Nom de type de contrôle**  
 Par défaut, le nom du type de contrôle est basé sur le nom court, suivi par `Control`. Par exemple, si votre contrôle court de nom est `Price`, le nom de type de classe de contrôle est `Price Control`. Si vous modifiez la valeur dans ce champ, assurez-vous que le nom indique un héritage.  
  
 **ID de type de contrôle**  
 Définit l’ID de type de contrôle de la classe du contrôle. Le contrôle, cette chaîne est consignée dans le Registre lorsqu’il est ajouté à un projet. Applications conteneur utilisent cette chaîne pour créer une instance du contrôle.  
  
 Par défaut, l’ID de type de contrôle est basé sur le nom du projet, que vous avez spécifié dans le **nouveau projet** boîte de dialogue et le nom court. Ce nom doit correspondre au nom de type.  
  
 Par défaut, l’ID de type de contrôle s’affiche comme suit :  
  
 *ProjectName.ShortName*CTRL.1.  
  
 Si vous modifiez le nom court dans cette boîte de dialogue, l’ID de type de contrôle s’affiche comme suit :  
  
 *ProjectName.NewShortName*CTRL.1.  
  
 **Nom de la classe PropPage**  
 Par défaut, le nom de la classe de page de propriétés est basé sur le nom court, avec `C` en tant que préfixe et `PropPage` comme suffixe. Par exemple, si votre contrôle court de nom est `Price`, le nom de classe de page de propriétés est `CPricePropPage`. Ce nom doit correspondre au nom de la classe du contrôle, avec `PropPage`.  
  
 **Fichier .h PropPage**  
 Par défaut, le nom du fichier d’en-tête de page propriété repose sur le nom court, avec comme un `PropPage` comme suffixe et `.h` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, nom de fichier en-tête de page de propriétés est `PricePropPage.h`. Ce nom doit correspondre au nom de la classe.  
  
 **Fichier .cpp de la page de Prop.**  
 Par défaut, le nom du fichier de mise en œuvre de page de propriétés est basé sur le nom court, avec comme un `PropPage` comme suffixe et `.cpp` en tant que l’extension de fichier. Par exemple, si votre contrôle court de nom est `Price`, nom de fichier en-tête de page de propriétés est `PricePropPage.cpp`. Ce nom doit correspondre le nom de fichier d’en-tête.  
  
 **Nom du type de page de Prop.**  
 Par défaut, le nom de type de page de propriétés est basé sur le nom court, suivi par `Property Page`. Par exemple, si votre contrôle court de nom est `Price`, le nom de type de page de propriétés est `Price Property Page`. Si vous modifiez la valeur dans ce champ, assurez-vous que le nom indique la classe du contrôle.  
  
 **ID du type de page de Prop.**  
 Définit l’ID de la classe de page de propriétés. Le contrôle, cette chaîne est consignée dans le Registre lorsqu’il est appliqué à un projet. Une application conteneur utilise cette chaîne pour créer une instance de la page de propriétés du contrôle.  
  
 Par défaut, l’ID de type de page de propriétés est basé sur le nom du projet, que vous avez spécifié dans le **nouveau projet** boîte de dialogue et le nom court. Ce nom doit correspondre au nom de type.  
  
 Par défaut, l’ID de type de page de propriétés apparaît comme suit :  
  
 *ProjectName.ShortName*PropPage.1.  
  
 Si vous modifiez le nom court dans cette boîte de dialogue, l’ID de type de page de propriétés apparaît comme suit :  
  
 *ProjectName.NewShortName*PropPage.1.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Paramètres d’application, Assistant contrôle ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Paramètres du contrôle, Assistant contrôle ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)


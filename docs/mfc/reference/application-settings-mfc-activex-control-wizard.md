---
title: Paramètres d’application, Assistant contrôle ActiveX MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, application settings
ms.assetid: 48475194-cc63-467f-8499-f142269a4c1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad19a4c9726378a54bd68173decd2469c17ec75
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708565"
---
# <a name="application-settings-mfc-activex-control-wizard"></a>Paramètres de l’application, Assistant Contrôle ActiveX MFC
Utilisez cette page de l’Assistant Contrôle ActiveX MFC pour concevoir et ajouter des fonctionnalités de base à un nouveau projet ActiveX MFC. Ces paramètres s’appliquent à l’application elle-même, et non pas à une fonctionnalité ou un élément spécifique du contrôle.  
  
- **Licence d’exécution**

   Sélectionnez cette option pour générer un fichier de licence utilisateur à distribuer avec le contrôle. La licence est un fichier texte, *nom_projet*.lic. Ce fichier doit être dans le même répertoire que la DLL du contrôle, pour permettre la création d’une instance du contrôle dans un environnement au moment de la conception. Vous distribuez généralement ce fichier avec votre contrôle, mais vos clients ne le distribuent pas.  
  
- **Générer des fichiers d’aide**

   Sélectionnez cette option pour générer des fichiers d’aide faisant l’objet d’un stub et pour configurer le projet de façon à y inclure l’aide de votre contrôle. Un projet par défaut, créé sans cette option, génère seulement une boîte **À propos de** qui s’affiche quand l’utilisateur clique avec le bouton droit sur le contrôle, utilise la touche F1 ou clique sur **Aide** sur le conteneur du contrôle.  
  
   > [!NOTE]
   > La façon dont l’aide est affichée dépend de la façon dont votre contrôle interagit avec son conteneur. Si vous incluez l’aide avec votre conteneur, vous devez gérer les messages entre le contrôle et le conteneur pour afficher l’aide de façon appropriée.  
  
   Quand vous générez des fichiers d’aide à l’aide de l’Assistant, votre projet inclut les éléments suivants :  
  
   - Le fichier .vcxproj contient le code pour générer et configurer le fichier d’aide quand le projet est généré.  
  
   - Le fichier *Page_propriétés_nom_projet*.cpp inclut une [SetHelpInfo](../../mfc/reference/colepropertypage-class.md#sethelpinfo) fonction dans le constructeur.  
  
   - Le fichier nom_projet.hpj est le fichier d’aide du projet utilisé par le compilateur d’aide pour créer le fichier d’aide du contrôle ActiveX. Le fichier .hpj est un fichier texte contenant les informations sur la création de votre fichier d’aide et les chemins des fichiers supplémentaires (par exemple les bitmaps) inclus dans le fichier d’aide.  
  
   - Le projet inclut le répertoire HLP destiné à contenir les fichiers bitmap d’aide du projet et le fichier de rubriques d’aide (*nom_projet*.rtf). Ce fichier de rubriques d’aide contient les rubriques d’aide standard pour les propriétés, événements et méthodes courants pris en charge par de nombreux contrôles ActiveX. Vous pouvez modifier ce fichier .rtf pour ajouter ou supprimer des rubriques d’aide spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Noms du contrôle, Assistant contrôle ActiveX MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)   
 [Paramètres du contrôle, Assistant Contrôle ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)


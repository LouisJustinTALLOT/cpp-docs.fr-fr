---
title: "Création d’un contrôle ActiveX MFC | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.activex.project
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
ms.assetid: 8bd5a93c-d04d-414e-bb28-163fdc1c0dd5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 47207d80fc36b8f80fafbb495fa9592312bde09c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-mfc-activex-control"></a>Création d'un contrôle ActiveX MFC
Programmes de contrôle ActiveX sont modulaire conçu pour permettre à un type spécifique de fonctionnalités à une application parente. Par exemple, vous pouvez créer un contrôle tel qu’un bouton pour une utilisation dans une boîte de dialogue ou une barre d’outils pour une utilisation dans une page Web.  
  
 Pour créer un contrôle ActiveX MFC, le plus simple consiste à utiliser le [Assistant contrôle ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md).  
  
### <a name="to-create-an-mfc-activex-control-using-the-mfc-activex-control-wizard"></a>Pour créer un contrôle ActiveX de MFC à l’aide de l’Assistant de contrôle ActiveX MFC  
  
1.  Suivez les instructions de la rubrique d’aide [création d’un projet avec l’Assistant Application Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  Dans le **nouveau projet** boîte de dialogue, sélectionnez le **contrôle ActiveX MFC** icône dans le volet Modèles pour ouvrir l’Assistant contrôle ActiveX MFC.  
  
3.  Définir votre [paramètres de l’application](../../mfc/reference/application-settings-mfc-activex-control-wizard.md), [des noms de contrôle](../../mfc/reference/control-names-mfc-activex-control-wizard.md), et [contrôler les paramètres](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) à l’aide de l’Assistant de contrôle ActiveX MFC.  
  
    > [!NOTE]
    >  Ignorez cette étape afin que l'Assistant conserve les paramètres par défaut.  
  
4.  Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir votre nouveau projet dans l’environnement de développement.  
  
 Après avoir créé votre projet, vous pouvez afficher les fichiers créés dans **l’Explorateur de solutions**. Pour plus d'informations sur les fichiers créés par l'Assistant pour votre projet, consultez le fichier Readme.txt généré pour le projet. Pour plus d’informations sur les types de fichiers, consultez [Types de fichiers créés pour les projets Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
 Après avoir créé votre projet, vous pouvez utiliser les Assistants code pour ajouter [fonctions](../../ide/add-member-function-wizard.md), [variables](../../ide/add-member-variable-wizard.md), [événements](../../ide/add-event-wizard.md), [propriétés](../../ide/names-add-property-wizard.md), et [méthodes](../../ide/add-method-wizard.md). Pour plus d’informations sur la personnalisation de votre contrôle ActiveX, consultez [contrôles ActiveX MFC](../../mfc/mfc-activex-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Pages de propriétés](../../ide/property-pages-visual-cpp.md)   
 [Déploiement d’Applications](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)


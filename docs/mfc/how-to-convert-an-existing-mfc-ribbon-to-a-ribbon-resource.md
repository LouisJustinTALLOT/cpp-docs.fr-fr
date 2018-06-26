---
title: 'Comment : convertir un ruban MFC existant en ressource de ruban | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource, converting from an MFC ribbon
- MFC ribbon, converting to a ribbon resource
ms.assetid: 324b7ff6-58f9-4691-96a9-9836a79d0fb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2551709652df0e0c65b1b0b6b5085550044e9966
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928995"
---
# <a name="how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource"></a>Comment : convertir un ruban MFC existant en ressource du ruban
Ressources de ruban sont plus faciles à visualiser, modifier et gérer que les rubans codés manuellement. Cette rubrique décrit comment convertir un ruban codé manuellement dans un projet MFC dans une ressource de ruban.  
  
 Vous devez disposer d’un projet MFC existant qui comporte du code qui utilise les classes de ruban MFC, par exemple, [classe CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md).  
  
### <a name="to-convert-an-mfc-ribbon-to-a-ribbon-resource"></a>Pour convertir un ruban MFC à une ressource de ruban  
  
1.  Dans Visual Studio, dans un projet MFC existant, ouvrez le fichier source où le `CMFCRibbonBar` l’objet est initialisé. En règle générale, le fichier est mainfrm.cpp. Ajoutez le code suivant après le code d’initialisation pour le ruban.  
  
 ```  
    m_wndRibbonBar.SaveToXMLFile("RibbonOutput.xml");

 ```  
  
     Enregistrez et fermez le fichier.  
  
2.  Générez et exécutez l’application MFC, puis dans le bloc-notes, ouvrez RibbonOutput.txt et copiez son contenu.  
  
3.  Dans Visual Studio, sur le **projet** menu, cliquez sur **ajouter une ressource**. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **ruban** puis cliquez sur **nouveau**.  
  
     Visual Studio crée une ressource de ruban et s’ouvre en mode Création. L’ID de ressource de ruban est IDR_RIBBON1, qui est affichée dans **affichage des ressources**. Le ruban est défini dans le fichier XML ribbon1.mfcribbon-ms.  
  
4.  Dans Visual Studio, ouvrez ribbon1.mfcribbon-ms, supprimez son contenu, puis collez le contenu du RibbonOutput.txt, ce qui vous avez copiée précédemment. Enregistrez et fermez ribbon1.mfcribbon-ms.  
  
5.  À nouveau d’ouvrir le fichier source où l’objet CMFCRibbonBar est initialisé (généralement, mainfrm.cpp) et commentez existants code du ruban. Ajoutez le code suivant après le code mis en commentaire.  
  
 ```  
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);

 ```  
  
6.  Générez le projet et exécuter le programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)


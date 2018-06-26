---
title: 'Comment : ajouter la prise en charge du Gestionnaire de redémarrage | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f11cc3258d577969807dd63c24c00da39652fff
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931271"
---
# <a name="how-to-add-restart-manager-support"></a>Comment : ajouter la prise en charge du Gestionnaire de redémarrage

Le Gestionnaire de redémarrage est une fonctionnalité ajoutée à Visual Studio pour Windows Vista ou des systèmes d’exploitation ultérieurs. Le Gestionnaire de redémarrage prend en charge votre application, si elle se ferme ou redémarre de façon inattendue. Le comportement du Gestionnaire de redémarrage dépend du type de votre application. Si votre application est un éditeur de documents, le Gestionnaire de redémarrage permet à votre application d’enregistrer automatiquement l’état et le contenu des documents ouverts. Par ailleurs, il redémarre votre application après une fermeture inattendue. Si votre application n’est pas un éditeur de documents, le Gestionnaire de redémarrage la redémarre. Toutefois, il ne peut pas enregistrer l’état de l’application par défaut.  
  
 Après avoir redémarré, l’application affiche une boîte de dialogue de tâches si l’application est au format Unicode. S’il s’agit d’une application ANSI, celle-ci affiche une boîte de message Windows. À ce stade, l’utilisateur choisit de restaurer ou non les documents enregistrés automatiquement. Si l’utilisateur ne restaure pas les documents enregistrés automatiquement, le Gestionnaire de redémarrage ignore les fichiers temporaires.  
  
> [!NOTE]
>  Vous pouvez substituer le comportement par défaut du Gestionnaire de redémarrage pour l’enregistrement des données et le redémarrage de l’application.  
  
 Par défaut, les applications MFC créées à l’aide de l’Assistant projet dans [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] prend en charge le Gestionnaire de redémarrage lorsque les applications sont exécutées sur un ordinateur équipé de Windows Vista ou système d’exploitation ultérieur. Si vous ne souhaitez pas que votre application prenne en charge le Gestionnaire de redémarrage, vous pouvez le désactiver dans l’Assistant Nouveau projet.  
  
### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Pour ajouter la prise en charge du Gestionnaire de redémarrage à une application existante  
  
1.  Ouvrez une application MFC existante dans [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
2.  Ouvrez le fichier source de votre application principale. Par défaut, il s’agit du fichier .cpp qui porte le même nom que votre application. Par exemple, le fichier source de l’application principale pour MyProject est MyProject.cpp.  
  
3.  Recherchez le constructeur de votre application principale. Par exemple, si votre projet est MyProject, le constructeur est `CMyProjectApp::CMyProjectApp()`.  
  
4.  Ajoutez la ligne de code suivante à votre constructeur.  
  
 ```  
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;  
 ```  
  
5.  Assurez-vous que la méthode `InitInstance` de votre application appelle sa méthode `InitInstance` parente : [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) ou `CWinAppEx::InitInstance`. Le `InitInstance` (méthode) est chargée de vérifier la *m_dwRestartManagerSupportFlags* paramètre.  
  
6.  Compilez et exécutez votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CDataRecoveryHandler](../mfc/reference/cdatarecoveryhandler-class.md)   
 [CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)   
 [CWinApp (classe)](../mfc/reference/cwinapp-class.md)   
 [CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)   
 [CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)


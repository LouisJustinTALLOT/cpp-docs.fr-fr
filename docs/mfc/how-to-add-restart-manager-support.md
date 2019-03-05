---
title: 'Procédure : Ajouter la prise en charge du Gestionnaire de redémarrage'
ms.date: 11/04/2016
helpviewer_keywords:
- Restart manager [MFC]
- C++, application crash support
ms.assetid: 7f3f5867-d4bc-4ba8-b3c9-dc1e7be93642
ms.openlocfilehash: 23f860c43c63e3153f4b87f8eaf05d61709af82f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57279781"
---
# <a name="how-to-add-restart-manager-support"></a>Procédure : Ajouter la prise en charge du Gestionnaire de redémarrage

Le Gestionnaire de redémarrage est une fonctionnalité ajoutée à Visual Studio pour Windows Vista ou des systèmes d’exploitation ultérieurs. Le Gestionnaire de redémarrage prend en charge votre application, si elle se ferme ou redémarre de façon inattendue. Le comportement du Gestionnaire de redémarrage dépend du type de votre application. Si votre application est un éditeur de documents, le Gestionnaire de redémarrage permet à votre application d’enregistrer automatiquement l’état et le contenu des documents ouverts. Par ailleurs, il redémarre votre application après une fermeture inattendue. Si votre application n’est pas un éditeur de documents, le Gestionnaire de redémarrage la redémarre. Toutefois, il ne peut pas enregistrer l’état de l’application par défaut.

Après avoir redémarré, l’application affiche une boîte de dialogue de tâches si l’application est au format Unicode. S’il s’agit d’une application ANSI, celle-ci affiche une boîte de message Windows. À ce stade, l’utilisateur choisit de restaurer ou non les documents enregistrés automatiquement. Si l’utilisateur ne restaure pas les documents enregistrés automatiquement, le Gestionnaire de redémarrage ignore les fichiers temporaires.

> [!NOTE]
>  Vous pouvez substituer le comportement par défaut du Gestionnaire de redémarrage pour l’enregistrement des données et le redémarrage de l’application.

Par défaut, les applications MFC créées à l’aide de l’Assistant de projet dans Visual Studio prend en charge le Gestionnaire de redémarrage quand les applications sont exécutées sur un ordinateur disposant d’un Windows Vista ou une version ultérieure du système d’exploitation. Si vous ne souhaitez pas que votre application prenne en charge le Gestionnaire de redémarrage, vous pouvez le désactiver dans l’Assistant Nouveau projet.

### <a name="to-add-support-for-the-restart-manager-to-an-existing-application"></a>Pour ajouter la prise en charge du Gestionnaire de redémarrage à une application existante

1. Ouvrez une application MFC existante dans Visual Studio.

1. Ouvrez le fichier source de votre application principale. Par défaut, il s’agit du fichier .cpp qui porte le même nom que votre application. Par exemple, le fichier source de l’application principale pour MyProject est MyProject.cpp.

1. Recherchez le constructeur de votre application principale. Par exemple, si votre projet est MyProject, le constructeur est `CMyProjectApp::CMyProjectApp()`.

1. Ajoutez la ligne de code suivante à votre constructeur.

```
    m_dwRestartManagerSupportFlags = AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS;
```

1. Assurez-vous que le `InitInstance` méthode de votre application appelle son parent `InitInstance` méthode : [CWinApp::InitInstance](../mfc/reference/cwinapp-class.md#initinstance) ou `CWinAppEx::InitInstance`. Le `InitInstance` (méthode) est chargée de vérifier la *m_dwRestartManagerSupportFlags* paramètre.

1. Compilez et exécutez votre application.

## <a name="see-also"></a>Voir aussi

[CDataRecoveryHandler, classe](../mfc/reference/cdatarecoveryhandler-class.md)<br/>
[CWinApp::m_dwRestartManagerSupportFlags](../mfc/reference/cwinapp-class.md#m_dwrestartmanagersupportflags)<br/>
[CWinApp, classe](../mfc/reference/cwinapp-class.md)<br/>
[CWinApp::m_nAutosaveInterval](../mfc/reference/cwinapp-class.md#m_nautosaveinterval)<br/>
[CDocument::OnDocumentEvent](../mfc/reference/cdocument-class.md#ondocumentevent)

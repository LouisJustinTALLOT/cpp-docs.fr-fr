---
title: Outils définis par l’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b78e9a4fefad884f4ac683cd0c7f18688a5bdfe
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950812"
---
# <a name="user-defined-tools"></a>Outils définis par l'utilisateur
MFC prend en charge les outils définis par l'utilisateur. Un outil défini par l'utilisateur est une commande spéciale qui exécute un programme externe spécifié par l'utilisateur. Vous pouvez utiliser le processus de personnalisation pour gérer les outils définis par l'utilisateur. Toutefois, vous ne pouvez pas utiliser ce processus si votre objet d’application n’est pas dérivée de [CWinAppEx classe](../mfc/reference/cwinappex-class.md). Pour plus d’informations sur la personnalisation, consultez [personnalisation pour MFC](../mfc/customization-for-mfc.md).  
  
 Si vous avez activé la prise en charge des outils définis par l’utilisateur, la boîte de dialogue de personnalisation inclut automatiquement la **outils** onglet. L’illustration suivante montre le **outils** page.  
  
 ![Outils d’onglet dans la boîte de dialogue Personnaliser](../mfc/media/custdialogboxtoolstab.png "custdialogboxtoolstab")  
Onglet Outils de la boîte de dialogue de personnalisation  
  
## <a name="enabling-user-defined-tools-support"></a>Activation de la prise en charge des outils définis par l'utilisateur  
 Pour activer les outils définis par l’utilisateur dans une application, appelez [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Toutefois, vous devez d'abord définir plusieurs constantes dans les fichiers de ressources de votre application à utiliser comme paramètres pour cet appel.  
  
 Dans l'éditeur de ressources, créez une commande factice qui utilise un ID de commande approprié. Dans l’exemple suivant, nous utilisons `ID_TOOLS_ENTRY` en tant que l’ID de commande. Cet ID de commande marque un emplacement dans un ou plusieurs menus où le framework insérera les outils définis par l'utilisateur.  
  
 Vous devez mettre de côté certains ID consécutifs dans la table de chaînes pour représenter les outils définis par l'utilisateur. Le nombre de chaînes à mettre de côté est égal au nombre maximal d'outils utilisateur que les utilisateurs peuvent définir. Dans l'exemple suivant, ceux-ci sont nommés `ID_USER_TOOL1` à `ID_USER_TOOL10`.  
  
 Vous pouvez faire des suggestions aux utilisateurs pour les aider à sélectionner des répertoires et des arguments pour les programmes externes qui seront appelés en tant qu'outils. Pour cela, créez deux menus contextuels dans l'éditeur de ressources. Dans l'exemple suivant, ceux-ci sont nommés `IDR_MENU_ARGS` et `IDR_MENU_DIRS`. Pour chaque commande dans ces menus, définissez une chaîne dans la table de chaînes de votre application. L'ID de ressource de la chaîne doit être égal à l'ID de commande.  
  
 Vous pouvez également créer une classe dérivée de [CUserTool classe](../mfc/reference/cusertool-class.md) pour remplacer l’implémentation par défaut. Pour ce faire, passer les informations de runtime pour votre classe dérivée en tant que quatrième paramètre dans CWinAppEx::EnableUserTools, au lieu de RUNTIME_CLASS ([CUserTool classe](../mfc/reference/cusertool-class.md)).  
  
 Après avoir défini les constantes appropriées, appelez [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils définis par l’utilisateur.  
  
 L'appel de méthode suivant montre comment utiliser ces constantes :  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]  
  
 Dans cet exemple, l’onglet Outils est inclus dans le **personnalisation** boîte de dialogue. Le framework remplace toute commande correspondant à l'ID de commande `ID_TOOLS_ENTRY` dans un menu par l'ensemble des outils utilisateur actuellement définis lorsqu'un utilisateur ouvre ce menu. Les ID de commande `ID_USER_TOOL1` à `ID_USER_TOOL10` sont réservés à l'utilisation des outils définis par l'utilisateur. La classe [CUserTool classe](../mfc/reference/cusertool-class.md) gère les appels aux outils utilisateur. L’onglet de l’outil de la **personnalisation** boîte de dialogue fournit des boutons à droite des champs d’entrée argument et le répertoire pour accéder aux menus **IDR_MENU_ARGS** et **IDR_MENU_DIRS**. Lorsqu’un utilisateur sélectionne une commande à partir d’un de ces menus, le framework ajoute à la zone de texte à la chaîne qui a l’ID de ressource égal à l’ID de commande.  
  
### <a name="including-predefined-tools"></a>Ajout d'outils prédéfinis  
 Si vous souhaitez prédéfinir des outils sur le démarrage de l’application, vous devez substituer la [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) (méthode) de la fenêtre principale de votre application. Dans cette méthode, vous devez effectuer les étapes suivantes :  
  
##### <a name="to-add-new-tools-in-loadframe"></a>Pour ajouter de nouveaux outils dans LoadFrame  
  
1.  Obtenir un pointeur vers le [CUserToolsManager classe](../mfc/reference/cusertoolsmanager-class.md) objet en appelant [CWinAppEx::GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).  
  
2.  Pour tous les outils que vous souhaitez créer, appelez [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Cette méthode retourne un pointeur vers un [CUserTool classe](../mfc/reference/cusertool-class.md) de l’objet et l’ajoute à la collection interne des outils utilisateur nouvellement créé. Si vous avez fourni les informations d’exécution d’une classe dérivée de [CUserTool classe](../mfc/reference/cusertool-class.md) en tant que quatrième paramètre de [CWinAppEx::EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager::CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) instancie et retourner une instance de cette classe à la place.  
  
3.  Pour chaque outil, définissez son étiquette de texte en paramétrant `CUserTool::m_strLabel` et définissez sa commande en appelant `CUserTool::SetCommand`. L’implémentation par défaut de [CUserTool classe](../mfc/reference/cusertool-class.md) récupère automatiquement les icônes disponibles à partir du programme qui est spécifié dans l’appel à `SetCommand`.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation pour MFC](../mfc/customization-for-mfc.md)   
 [Classe de CUserTool](../mfc/reference/cusertool-class.md)   
 [Classe de CUserToolsManager](../mfc/reference/cusertoolsmanager-class.md)   
 [CWinAppEx, classe](../mfc/reference/cwinappex-class.md)





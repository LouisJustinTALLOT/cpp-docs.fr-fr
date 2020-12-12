---
description: En savoir plus sur les outils définis par l’utilisateur
title: Outils définis par l'utilisateur
ms.date: 11/19/2018
helpviewer_keywords:
- user-defined tools (MFC Extensions)
ms.assetid: cb887421-78ce-4652-bc67-96a53984ccaa
ms.openlocfilehash: 4cccd0a68751a2f196c8c2e652088e8939e3f162
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263632"
---
# <a name="user-defined-tools"></a>Outils définis par l'utilisateur

MFC prend en charge les outils définis par l'utilisateur. Un outil défini par l'utilisateur est une commande spéciale qui exécute un programme externe spécifié par l'utilisateur. Vous pouvez utiliser le processus de personnalisation pour gérer les outils définis par l'utilisateur. Toutefois, vous ne pouvez pas utiliser ce processus si votre objet application n’est pas dérivé de la [classe CWinAppEx](../mfc/reference/cwinappex-class.md). Pour plus d’informations sur la personnalisation, consultez [personnalisation pour MFC](../mfc/customization-for-mfc.md).

Si vous avez activé la prise en charge des outils définis par l’utilisateur, la boîte de dialogue Personnalisation comprend automatiquement l’onglet **Outils** . L’illustration suivante montre la page **Outils** .

![Onglet Outils de la boîte de dialogue Personnalisation](../mfc/media/custdialogboxtoolstab.png "Onglet Outils de la boîte de dialogue Personnalisation") <br/>
Onglet Outils de la boîte de dialogue de personnalisation

## <a name="enabling-user-defined-tools-support"></a>Activation de la prise en charge des outils définis par l'utilisateur

Pour activer les outils définis par l’utilisateur dans une application, appelez [CWinAppEx :: EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools). Toutefois, vous devez d'abord définir plusieurs constantes dans les fichiers de ressources de votre application à utiliser comme paramètres pour cet appel.

Dans l'éditeur de ressources, créez une commande factice qui utilise un ID de commande approprié. Dans l’exemple suivant, nous utilisons `ID_TOOLS_ENTRY` comme ID de commande. Cet ID de commande marque un emplacement dans un ou plusieurs menus où le framework insérera les outils définis par l'utilisateur.

Vous devez mettre de côté certains ID consécutifs dans la table de chaînes pour représenter les outils définis par l'utilisateur. Le nombre de chaînes à mettre de côté est égal au nombre maximal d'outils utilisateur que les utilisateurs peuvent définir. Dans l'exemple suivant, ceux-ci sont nommés `ID_USER_TOOL1` à `ID_USER_TOOL10`.

Vous pouvez faire des suggestions aux utilisateurs pour les aider à sélectionner des répertoires et des arguments pour les programmes externes qui seront appelés en tant qu’outils. Pour cela, créez deux menus contextuels dans l'éditeur de ressources. Dans l'exemple suivant, ceux-ci sont nommés `IDR_MENU_ARGS` et `IDR_MENU_DIRS`. Pour chaque commande dans ces menus, définissez une chaîne dans la table de chaînes de votre application. L'ID de ressource de la chaîne doit être égal à l'ID de commande.

Vous pouvez également créer une classe dérivée à partir de la [classe CUserTool](../mfc/reference/cusertool-class.md) pour remplacer l’implémentation par défaut. Pour ce faire, transmettez les informations d’exécution de votre classe dérivée en tant que quatrième paramètre dans CWinAppEx :: EnableUserTools, au lieu de RUNTIME_CLASS ([classe CUserTool](../mfc/reference/cusertool-class.md)).

Après avoir défini les constantes appropriées, appelez [CWinAppEx :: EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools) pour activer les outils définis par l’utilisateur.

L'appel de méthode suivant montre comment utiliser ces constantes :

[!code-cpp[NVC_MFC_VisualStudioDemo#1](../mfc/codesnippet/cpp/user-defined-tools_1.cpp)]

Dans cet exemple, l’onglet outils sera inclus dans la boîte de dialogue **personnalisation** . Le framework remplace toute commande correspondant à l'ID de commande `ID_TOOLS_ENTRY` dans un menu par l'ensemble des outils utilisateur actuellement définis lorsqu'un utilisateur ouvre ce menu. Les ID de commande `ID_USER_TOOL1` à `ID_USER_TOOL10` sont réservés à l'utilisation des outils définis par l'utilisateur. La classe [CUserTool](../mfc/reference/cusertool-class.md) classe gère les appels aux outils utilisateur. L’onglet outil de la boîte de dialogue **personnalisation** fournit des boutons à droite des champs d’entrée d’argument et de répertoire pour accéder aux menus **IDR_MENU_ARGS** et **IDR_MENU_DIRS**. Quand un utilisateur sélectionne une commande dans l’un de ces menus, le Framework ajoute à la zone de texte appropriée la chaîne dont l’ID de ressource est égal à l’ID de commande.

### <a name="including-predefined-tools"></a>Ajout d'outils prédéfinis

Si vous souhaitez prédéfinir certains outils au démarrage de l’application, vous devez remplacer la méthode [CFrameWnd :: LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) de la fenêtre principale de votre application. Dans cette méthode, vous devez effectuer les étapes suivantes :

##### <a name="to-add-new-tools-in-loadframe"></a>Pour ajouter de nouveaux outils dans LoadFrame

1. Obtenez un pointeur vers l’objet de [classe CUserToolsManager](../mfc/reference/cusertoolsmanager-class.md) en appelant [CWinAppEx :: GetUserToolsManager](../mfc/reference/cwinappex-class.md#getusertoolsmanager).

1. Pour chaque outil que vous souhaitez créer, appelez [CUserToolsManager :: CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool). Cette méthode retourne un pointeur vers un objet de [classe CUserTool](../mfc/reference/cusertool-class.md) et ajoute l’outil utilisateur nouvellement créé à la collection interne d’outils. Si vous avez fourni les informations d’exécution pour une classe dérivée de la [classe CUserTool](../mfc/reference/cusertool-class.md) en tant que quatrième paramètre de [CWinAppEx :: EnableUserTools](../mfc/reference/cwinappex-class.md#enableusertools), [CUserToolsManager :: CreateNewTool](../mfc/reference/cusertoolsmanager-class.md#createnewtool) instancie et retourne une instance de cette classe à la place.

1. Pour chaque outil, définissez son étiquette de texte en paramétrant `CUserTool::m_strLabel` et définissez sa commande en appelant `CUserTool::SetCommand`. L’implémentation par défaut de la [classe CUserTool](../mfc/reference/cusertool-class.md) récupère automatiquement les icônes disponibles à partir du programme qui est spécifié dans l’appel à `SetCommand` .

## <a name="see-also"></a>Voir aussi

[Personnalisation pour MFC](../mfc/customization-for-mfc.md)<br/>
[CUserTool, classe](../mfc/reference/cusertool-class.md)<br/>
[CUserToolsManager, classe](../mfc/reference/cusertoolsmanager-class.md)<br/>
[CWinAppEx, classe](../mfc/reference/cwinappex-class.md)

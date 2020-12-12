---
description: 'En savoir plus sur : relations entre les objets MFC'
title: Relations entre les objets MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: 0646d487d1d60293461316edddcb97fde30905a8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218054"
---
# <a name="relationships-among-mfc-objects"></a>Relations entre les objets MFC

Pour aider à mettre le processus de création de document/vue en perspective, envisagez d'utiliser un programme en cours d'exécution : un document, la fenêtre frame utilisée pour contenir la vue, puis la vue associée au document.

- Un document conserve une liste des vues de ce document et un pointeur vers le modèle de document qui a créé le document.

- Une vue conserve un pointeur à son document et est un enfant de la fenêtre frame parente.

- Une fenêtre frame de document conserve un pointeur vers la vue active actuelle.

- Un modèle de document conserve une liste des documents ouverts.

- L'application conserve une liste de ses modèles.

- Windows gère toutes les fenêtres actives et peut donc envoyer des messages à celles-ci.

Ces relations sont établies lors de la création de document/vue. Le tableau suivant montre comment les objets d'un programme en cours d'exécution peuvent accéder à d'autres objets. Tout objet peut obtenir un pointeur vers l’objet d’application en appelant la fonction globale [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Accès à d'autres objets dans votre application

|À partir de l'objet|Comment accéder à d'autres objets|
|-----------------|---------------------------------|
|Document|Utilisez [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) et [GetNextView](../mfc/reference/cdocument-class.md#getnextview) pour accéder à la liste des vues du document.<br /><br /> Appelez [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) pour récupérer le modèle de document.|
|Affichage|Appelez [GetDocument](../mfc/reference/cview-class.md#getdocument) pour récupérer le document.<br /><br /> Appelez [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) pour accéder à la fenêtre frame.|
|Fenêtre frame de document|Appelez [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) pour obtenir la vue actuelle.<br /><br /> Appelez [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) pour obtenir le document attaché à la vue actuelle.|
|Fenêtre frame MDI|Appelez [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) pour accéder au [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)actuellement actif.|

En général, une fenêtre frame ne présente qu'une seule vue, mais dans certains cas, comme dans les fenêtres de fractionnement, la même fenêtre frame contient plusieurs vues. La fenêtre frame conserve un pointeur dans la vue actuellement active ; le pointeur est mis à jour lorsqu'une vue est activée.

> [!NOTE]
> Un pointeur vers la fenêtre frame principale est stocké dans la variable membre [m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) de l’objet application. Un appel à `OnFileNew` dans votre substitution de la `InitInstance` fonction membre de `CWinApp` définit *m_pMainWnd* pour vous. Si vous n'appelez pas `OnFileNew`, vous devez définir la valeur de la variable dans `InitInstance` vous-même. (Les applications de composant COM SDI (serveur) peuvent ne pas définir la variable si/Embedding est sur la ligne de commande.) Notez que *m_pMainWnd* est désormais membre de la classe `CWinThread` plutôt que `CWinApp` .

## <a name="see-also"></a>Voir aussi

[Modèles de document et processus de création de document/vue](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Création d’un modèle de document](../mfc/document-template-creation.md)<br/>
[Création de document/vue](../mfc/document-view-creation.md)<br/>
[Création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

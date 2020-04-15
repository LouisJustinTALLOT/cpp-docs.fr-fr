---
title: Relations entre les objets MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, relationships between key objects
- objects [MFC], relationships
- relationships, MFC objects
- MFC object relationships
ms.assetid: 6e8f3b51-e80f-4d88-94c8-4c1e4ee163ad
ms.openlocfilehash: d7e40e25b405d3f8ec50a518889cc2b89bc8c725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372812"
---
# <a name="relationships-among-mfc-objects"></a>Relations entre les objets MFC

Pour aider à mettre le processus de création de document/vue en perspective, envisagez d'utiliser un programme en cours d'exécution : un document, la fenêtre frame utilisée pour contenir la vue, puis la vue associée au document.

- Un document conserve une liste des vues de ce document et un pointeur vers le modèle de document qui a créé le document.

- Une vue conserve un pointeur à son document et est un enfant de la fenêtre frame parente.

- Une fenêtre frame de document conserve un pointeur vers la vue active actuelle.

- Un modèle de document conserve une liste des documents ouverts.

- L'application conserve une liste de ses modèles.

- Windows gère toutes les fenêtres actives et peut donc envoyer des messages à celles-ci.

Ces relations sont établies lors de la création de document/vue. Le tableau suivant montre comment les objets d'un programme en cours d'exécution peuvent accéder à d'autres objets. N’importe quel objet peut obtenir un pointeur à l’objet d’application en appelant la fonction globale [AfxGetApp](../mfc/reference/application-information-and-management.md#afxgetapp).

### <a name="gaining-access-to-other-objects-in-your-application"></a>Accès à d'autres objets dans votre application

|À partir de l'objet|Comment accéder à d'autres objets|
|-----------------|---------------------------------|
|Document|Utilisez [GetFirstViewPosition](../mfc/reference/cdocument-class.md#getfirstviewposition) et [GetNextView](../mfc/reference/cdocument-class.md#getnextview) pour accéder à la liste de vues du document.<br /><br /> Appelez [GetDocTemplate](../mfc/reference/cdocument-class.md#getdoctemplate) pour obtenir le modèle de document.|
|Affichage|Appelez [GetDocument](../mfc/reference/cview-class.md#getdocument) pour obtenir le document.<br /><br /> Appelez [GetParentFrame](../mfc/reference/cwnd-class.md#getparentframe) pour obtenir la fenêtre du cadre.|
|Fenêtre frame de document|Appelez [GetActiveView](../mfc/reference/cframewnd-class.md#getactiveview) pour obtenir la vue actuelle.<br /><br /> Appelez [GetActiveDocument](../mfc/reference/cframewnd-class.md#getactivedocument) pour joindre le document à la vue actuelle.|
|Fenêtre frame MDI|Appelez [MDIGetActive](../mfc/reference/cmdiframewnd-class.md#mdigetactive) pour obtenir le [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)actuellement actif .|

En général, une fenêtre frame ne présente qu'une seule vue, mais dans certains cas, comme dans les fenêtres de fractionnement, la même fenêtre frame contient plusieurs vues. La fenêtre frame conserve un pointeur dans la vue actuellement active ; le pointeur est mis à jour lorsqu'une vue est activée.

> [!NOTE]
> Un pointeur vers la fenêtre du cadre principal est stocké dans la [variable m_pMainWnd](../mfc/reference/cwinthread-class.md#m_pmainwnd) membre de l’objet d’application. Un appel `OnFileNew` à votre remplacement `InitInstance` de `CWinApp` la fonction membre des ensembles *m_pMainWnd* pour vous. Si vous n'appelez pas `OnFileNew`, vous devez définir la valeur de la variable dans `InitInstance` vous-même. (SDI COM composant (serveur) applications peuvent ne pas définir la variable si /Embedding est sur la ligne de commande.) Notez que *m_pMainWnd* est maintenant un `CWinThread` membre `CWinApp`de la classe plutôt que .

## <a name="see-also"></a>Voir aussi

[Modèles de documents et processus de création de documents/vue](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Création de modèle de document](../mfc/document-template-creation.md)<br/>
[Création d'un document/d'une vue](../mfc/document-view-creation.md)<br/>
[Création de nouveaux documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

---
description: 'En savoir plus sur : TN025 : création d’un document, d’une vue et d’un frame'
title: 'TN025 : création de document, vue et frame'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 034c3670df57de03cf7db8f713937f3d433fbb56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215740"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025 : création de document, vue et frame

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les problèmes de conception et de propriété liés aux objets WinApp, objets DocTemplate, documents, frames et vues.

## <a name="winapp"></a>WinApp

Le système contient un objet `CWinApp`.

Il est statiquement construit et initialisé par l'implémentation interne de le framework de `WinMain`. Vous devez dériver de `CWinApp` pour faire quelque chose d’utile (exception : les dll d’extension MFC ne doivent pas avoir d' `CWinApp` instance ; l’initialisation est effectuée dans à la `DllMain` place).

L'objet `CWinApp` possède une liste de modèles de document (`CPtrList`). Il existe un ou plusieurs modèles de document par application. Les modèles de documents (DocTemplates) sont généralement chargés à partir du fichier de ressources (autrement dit, un tableau de chaînes) dans `CWinApp::InitInstance`.

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

L'objet `CWinApp` possède toutes les fenêtres frame dans l'application. La fenêtre frame principale de l’application doit être stockée dans `CWinApp::m_pMainWnd` ; en général, vous définissez *m_pMainWnd* dans l' `InitInstance` implémentation si vous n’avez pas l’habitude de laisser AppWizard le faire pour vous. Pour l'interface monodocument (SDI), il s'agit d'un `CFrameWnd` qui fait office de fenêtre frame d'application principale et de fenêtre frame de document unique. Pour l'interface multidocument (MDI), il s'agit d'un frame MDI (classe `CMDIFrameWnd`) qui fait office de fenêtre frame d'application principale contenant tous les enfant `CFrameWnd`s. Chaque fenêtre enfant est de la classe `CMDIChildWnd` (dérivée de `CFrameWnd`) et est considérée comme l'une des multiples fenêtres frame de document.

## <a name="doctemplates"></a>DocTemplates

`CDocTemplate` est le créateur et le gestionnaire de documents. Il est propriétaire des documents qu'il crée. Si votre application utilise une approche basée sur les ressources décrite ci-dessous, il ne sera pas nécessaire d'effectuer une dérivation à partir de `CDocTemplate`.

Pour une application SDI, la classe `CSingleDocTemplate` fait le suivi d'un document ouvert. Pour une application MDI, la classe `CMultiDocTemplate` conserve une liste (`CPtrList`) de tous les documents actuellement ouverts créés à partir de ce modèle. `CDocTemplate::AddDocument` et `CDocTemplate::RemoveDocument` fournissent des fonctions membres virtuelles pour ajouter ou supprimer un document du modèle. `CDocTemplate` est un Friend de `CDocument` donc, nous pouvons définir le `CDocument::m_pDocTemplate` pointeur arrière protégé pour qu’il pointe vers le modèle de document qui a créé le document.

`CWinApp` gère l'implémentation par défaut de `OnFileOpen`, qui à son tour interrogera tous les modèles du document. L'implémentation inclut la recherche des documents déjà ouverts et la définition du format permettant d'ouvrir de nouveaux documents.

`CDocTemplate` gère la liaison d'interface utilisateur des documents et des frames.

`CDocTemplate` conserve le nombre de documents sans nom.

## <a name="cdocument"></a>CDocument

`CDocument`Appartient à un `CDocTemplate` .

Les documents ont une liste de vues actuellement ouvertes (dérivées de `CView`) qui affichent le document ( `CPtrList`).

Les documents ne créent pas/ne détruisent pas les vues, mais ils sont joints entre eux lorsqu’ils sont créés. Lorsqu'un document est fermé (autrement dit, via Fichier/Fermer), toutes les vues jointes sont fermées. Lorsque la dernière vue sur un document est fermée (autrement dit, Fenêtre/Fermer) le document est fermé.

Les interfaces `CDocument::AddView`, `RemoveView` sont utilisées pour contenir la liste des vues. `CDocument` est un Friend de `CView` afin que nous puissions définir le `CView::m_pDocument` pointeur arrière.

## <a name="cframewnd"></a>CFrameWnd

`CFrameWnd` (également appelé frame) joue le même rôle que dans MFC 1.0, mais désormais la classe `CFrameWnd` est conçue pour être utilisée dans de nombreux cas sans dériver une nouvelle classe. Les classes dérivées `CMDIFrameWnd` et `CMDIChildWnd` sont également améliorées, donc bon nombre de commandes standard sont déjà implémentées.

`CFrameWnd` est chargé de créer des fenêtres dans la zone cliente du frame. Normalement, il existe une fenêtre principale remplissant la zone cliente du frame.

Pour une fenêtre de frame MDI, la zone cliente est remplie avec le contrôle MDICLIENT qui est à son tour le parent de toutes les fenêtres frame enfants MDI. Pour une fenêtre frame SDI ou une fenêtre frame enfants MDI, la zone cliente est généralement remplie par un objet fenêtre `CView` dérivé. Dans le cas de `CSplitterWnd`, la zone cliente de la vue est remplie avec l'objet fenêtre `CSplitterWnd`, et les objets de fenêtre dérivés de `CView` (un par volet de fractionnement) sont créés en tant que fenêtres enfants de `CSplitterWnd`.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

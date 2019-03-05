---
title: 'TN025 : CRÉATION Document, vue et la création de Frame'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 4958e7c4ca2c3cf9eed6420d72d0399fa112098d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284682"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025 : CRÉATION Document, vue et la création de Frame

> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les problèmes de conception et de propriété liés aux objets WinApp, objets DocTemplate, documents, frames et vues.

## <a name="winapp"></a>WinApp

Le système contient un objet `CWinApp`.

Il est statiquement construit et initialisé par l'implémentation interne de le framework de `WinMain`. Vous devez dériver de `CWinApp` faire quelque chose d’utile (exception : DLL d’extension MFC ne doivent pas avoir un `CWinApp` instance — s’effectue dans `DllMain` à la place).

L'objet `CWinApp` possède une liste de modèles de document (`CPtrList`). Il existe un ou plusieurs modèles de document par application. Les modèles de documents (DocTemplates) sont généralement chargés à partir du fichier de ressources (autrement dit, un tableau de chaînes) dans `CWinApp::InitInstance`.

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

L'objet `CWinApp` possède toutes les fenêtres frame dans l'application. La fenêtre frame principale de l’application doit être stockée dans `CWinApp::m_pMainWnd`; vous définissez généralement *m_pMainWnd* dans le `InitInstance` implémentation si vous n’avez pas laissez AppWizard faire pour vous. Pour l'interface monodocument (SDI), il s'agit d'un `CFrameWnd` qui fait office de fenêtre frame d'application principale et de fenêtre frame de document unique. Pour l'interface multidocument (MDI), il s'agit d'un frame MDI (classe `CMDIFrameWnd`) qui fait office de fenêtre frame d'application principale contenant tous les enfant `CFrameWnd`s. Chaque fenêtre enfant est de la classe `CMDIChildWnd` (dérivée de `CFrameWnd`) et est considérée comme l'une des multiples fenêtres frame de document.

## <a name="doctemplates"></a>DocTemplates


  `CDocTemplate` est le créateur et le gestionnaire de documents. Il est propriétaire des documents qu'il crée. Si votre application utilise une approche basée sur les ressources décrite ci-dessous, il ne sera pas nécessaire d'effectuer une dérivation à partir de `CDocTemplate`.

Pour une application SDI, la classe `CSingleDocTemplate` fait le suivi d'un document ouvert. Pour une application MDI, la classe `CMultiDocTemplate` conserve une liste (`CPtrList`) de tous les documents actuellement ouverts créés à partir de ce modèle. `CDocTemplate::AddDocument` et `CDocTemplate::RemoveDocument` fournissent des fonctions membres virtuelles pour ajouter ou supprimer un document du modèle. `CDocTemplate` est une fonction friend de `CDocument` donc nous pouvons définir l’élément protégé `CDocument::m_pDocTemplate` pointeur arrière pour la diriger vers le modèle de document qui a créé le document.

`CWinApp` gère l'implémentation par défaut de `OnFileOpen`, qui à son tour interrogera tous les modèles du document. L'implémentation inclut la recherche des documents déjà ouverts et la définition du format permettant d'ouvrir de nouveaux documents.

`CDocTemplate` gère la liaison d'interface utilisateur des documents et des frames.

`CDocTemplate` conserve le nombre de documents sans nom.

## <a name="cdocument"></a>CDocument

Un `CDocument` est détenu par un `CDocTemplate`.

Les documents ont une liste de vues actuellement ouvertes (dérivées de `CView`) qui affichent le document ( `CPtrList`).

Les documents ne créent pas/ne détruisent pas les vues, mais ils sont joints entre eux lorsqu’ils sont créés. Lorsqu'un document est fermé (autrement dit, via Fichier/Fermer), toutes les vues jointes sont fermées. Lorsque la dernière vue sur un document est fermée (autrement dit, Fenêtre/Fermer) le document est fermé.

Les interfaces `CDocument::AddView`, `RemoveView` sont utilisées pour contenir la liste des vues. `CDocument` est une fonction friend de `CView` afin que nous pouvons définir le `CView::m_pDocument` pointeur arrière.

## <a name="cframewnd"></a>CFrameWnd


  `CFrameWnd` (également appelé frame) joue le même rôle que dans MFC 1.0, mais désormais la classe `CFrameWnd` est conçue pour être utilisée dans de nombreux cas sans dériver une nouvelle classe. Les classes dérivées `CMDIFrameWnd` et `CMDIChildWnd` sont également améliorées, donc bon nombre de commandes standard sont déjà implémentées.


  `CFrameWnd` est chargé de créer des fenêtres dans la zone cliente du frame. Normalement, il existe une fenêtre principale remplissant la zone cliente du frame.

Pour une fenêtre de frame MDI, la zone cliente est remplie avec le contrôle MDICLIENT qui est à son tour le parent de toutes les fenêtres frame enfants MDI. Pour une fenêtre frame SDI ou une fenêtre frame enfants MDI, la zone cliente est généralement remplie par un objet fenêtre `CView` dérivé. Dans le cas de `CSplitterWnd`, la zone cliente de la vue est remplie avec l'objet fenêtre `CSplitterWnd`, et les objets de fenêtre dérivés de `CView` (un par volet de fractionnement) sont créés en tant que fenêtres enfants de `CSplitterWnd`.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

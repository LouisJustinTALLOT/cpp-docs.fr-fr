---
title: 'TN041 : Migration de MFC / OLE1 vers MFC / OLE 2'
ms.date: 10/18/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- OLE1 [MFC]
- migrating OLE1 to OLE2
- migration [MFC], OLE1 to OLE2
- OLE2 [MFC]
- porting OLE1 to OLE2
- converting OLE1 to OLE2
- upgrading Visual C++ applications [MFC], OLE1 to OLE2
- TN041
ms.assetid: 67f55552-4b04-4ddf-af0b-4d9eaf5da957
ms.openlocfilehash: b398a1adbf2f47343eed076f32ade5bb2564cd52
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767975"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041 : Migration de MFC/OLE1 vers MFC/OLE 2

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

## <a name="general-issues-relating-to-migration"></a>Problèmes généraux liés à la Migration

Un des objectifs de conception pour les classes OLE 2 dans MFC 2.5 (et versions supérieures) était de conserver une grande partie de la même architecture mises en place dans MFC 2.0 pour la prise en charge OLE 1.0. Par conséquent, de nombreuses classes OLE mêmes dans MFC 2.0 existent toujours dans cette version de MFC (`COleDocument`, `COleServerDoc`, `COleClientItem`, `COleServerItem`). En outre, la plupart des API dans ces classes sont exactement les mêmes. Toutefois, OLE 2 diffère considérablement OLE 1.0 donc vous pouvez vous attendre que certains détails ont été modifiés. Si vous êtes familiarisé avec la prise en charge de MFC 2.0 OLE1, vous aurez l’impression à la maison avec 2.0 prise en charge MFC.

Si vous êtes en prenant une application MFC/OLE1 existante et en lui ajoutant des fonctionnalités OLE 2, vous devez lire cette note tout d’abord. Cette note aborde certains problèmes généraux, vous pouvez rencontrer lors du portage de vos fonctionnalités OLE1 vers MFC/OLE 2 et puis traite les problèmes découverts lors du portage de deux applications incluses dans MFC 2.0 : les exemples OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>Architecture Document/Vue MFC est Important

Si votre application n’utilise pas l’architecture Document/Vue de MFC et que vous souhaitez ajouter la prise en charge OLE 2 à votre application, est maintenant le temps pour déplacer vers le Document/Vue. De nombreux avantages d’OLE 2 classes de MFC sont uniquement réalisés une fois que votre application est à l’aide de l’architecture intégré et composants de la bibliothèque MFC.

Implémentation d’un serveur ou un conteneur sans utiliser l’architecture MFC est possible, mais pas recommandée.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Utiliser l’implémentation MFC au lieu de votre propre

Classes MFC » préprogrammé implémentation » comme `CToolBar`, `CStatusBar`, et `CScrollView` ont intégré code cas spécial pour la prise en charge OLE 2. Par conséquent, si vous pouvez utiliser ces classes dans votre application vous allez bénéficier l’efforts mis en œuvre les de leur OLE. Là encore, il est possible de « restauration par votre propre » classes ici à ces fins, mais il n’est pas conseillée. Si vous avez besoin implémenter une fonctionnalité similaire, le code source MFC est une référence excellente pour traiter certains des points plus fine OLE (en particulier lorsqu’il s’agit de l’activation sur place).

## <a name="examine-the-mfc-sample-code"></a>Examinez l’exemple de Code MFC

Il existe un nombre d’échantillons MFC qui incluent des fonctionnalités OLE. Chacune de ces applications implémente OLE à partir d’un angle différent :

- [HIERSVR](../overview/visual-cpp-samples.md) conçu principalement pour une utilisation en tant qu’une application serveur. Il a été inclus dans MFC version 2.0 comme une application MFC/OLE1 et a été déplacée vers MFC/OLE 2 et ensuite étendu telle qu’elle implémente des nombreuses fonctionnalités OLE disponibles dans OLE 2.

- [OCLIENT](../overview/visual-cpp-samples.md) il s’agit d’une application de conteneur autonome, destinée à illustrer un grand nombre des fonctionnalités OLE à partir d’un point de vue du conteneur. Il a été trop porté à partir de MFC version 2.0 et ensuite étendu pour prendre en charge la plupart des fonctionnalités OLE plus avancées, telles que les formats de Presse-papiers personnalisés et des liens vers des éléments incorporés.

- [DRAWCLI](../overview/visual-cpp-samples.md) cette application implémente prise en charge du conteneur OLE beaucoup comme le fait de OCLIENT, à ceci près que ce soit dans le cadre d’un programme de dessin orientée objet existant. Il vous montre comment implémenter la prise en charge du conteneur OLE et l’intégrer dans votre application existante.

- [SUPERPAD](../overview/visual-cpp-samples.md) cette application, mais aussi en cours d’une application autonome fine, est également un serveur OLE. La prise en charge du serveur qu’il implémente est tout à fait minimaliste. Intérêt particulier est comment il utilise les services de Presse-papiers OLE pour copier des données dans le Presse-papiers, mais utilise la fonctionnalité intégrée dans le contrôle d’édition « Windows » pour implémenter la fonctionnalité de coller du Presse-papiers. Cela indique un mélange intéressant de traditionnelle utilisation les API Windows, ainsi que l’intégration avec les API OLE nouvelle.

Pour plus d’informations sur les exemples d’applications, consultez le « MFC exemple Help ».

## <a name="case-study-oclient-from-mfc-20"></a>Étude de cas : OCLIENT de MFC 2.0

Comme indiqué ci-dessus, [OCLIENT](../overview/visual-cpp-samples.md) a été incluse dans MFC 2.0 et implémenté OLE avec MFC/OLE1. Les étapes auxquelles cette application a été initialement convertie pour utiliser les classes MFC/OLE 2 sont décrits ci-dessous. Un certain nombre de fonctionnalités ont été ajouté après que le port initial a été effectué pour mieux illustrer les classes MFC/OLE. Ces fonctionnalités ne sont pas couverts ici ; reportez-vous à l’exemple lui-même pour plus d’informations sur ces fonctionnalités avancées.

> [!NOTE]
> Les erreurs du compilateur et le processus pas à pas a été créé avec Visual C++ 2.0. Emplacements et messages d’erreur spécifiques peuvent ont été modifiés avec Visual C++ 4.0, mais les informations conceptuelles restent valides.

## <a name="getting-it-up-and-running"></a>Il route

L’approche adoptée pour le port de l’exemple OCLIENT vers MFC/OLE doit commencer par créer et de résolution des erreurs du compilateur évident qui entraîneront. Si vous prenez l’exemple OCLIENT de MFC 2.0 et compilez sous cette version de MFC, vous trouverez qu’il n’existe pas que de nombreuses erreurs à résoudre. Les erreurs dans l’ordre dans lequel elles se sont produites sont décrits ci-dessous.

## <a name="compile-and-fix-errors"></a>Compilation et correction des erreurs

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

Le premier concerne erreur `COleClientItem::Draw`. Dans MFC/OLE1, il a fallu plus de paramètres que prend la version MFC/OLE. Les paramètres supplémentaires étaient souvent pas nécessaire et généralement NULL (comme dans cet exemple). Cette version de MFC peut déterminer automatiquement les valeurs pour le lpWBounds lorsque la capture de données modifiées qui n’est dessinée dans est un périphérique de métafichier. En outre, le paramètre pFormatDC n’est plus nécessaire dans la mesure où le framework générera un à partir de la « attribut de contrôleur de domaine » du pDC passé. Pour résoudre ce problème, vous donc simplement supprimer les deux NULL supplémentaire des paramètres à l’appel de dessin.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Les erreurs ci-dessus résultat du fait que tous les `COleClientItem::CreateXXXX` fonctions dans MFC/OLE1 requis qu’un nom unique passé pour représenter l’élément. Il s’agissait d’une exigence de l’API OLE sous-jacent. Cela n’est pas nécessaire dans MFC/OLE 2 dans la mesure où OLE 2 n’utilise pas DDE comme mécanisme de communication sous-jacent (le nom a été utilisé dans les conversations DDE). Pour résoudre ce problème, vous pouvez supprimer le `CreateNewName` de fonction, ainsi que toutes les références à celui-ci. Il est facile de savoir ce que chaque fonction MFC/OLE attend dans cette version simplement en plaçant votre curseur sur l’appel et en appuyant sur F1.

Un autre domaine qui est très différent est la gestion de Presse-papiers OLE 2. Avec OLE1, vous avez utilisé le Presse-papiers Windows Qu'api interagissent avec le Presse-papiers. Avec OLE 2, cela est effectué avec un mécanisme différent. Les API MFC/OLE1 supposé que le Presse-papiers était ouvert avant de copier un `COleClientItem` objet dans le Presse-papiers. Cela n’est plus nécessaire et entraîne l’échec de toutes les opérations de Presse-papiers MFC/OLE. Lorsque vous modifiez le code pour supprimer les dépendances sur `CreateNewName`, vous devez également supprimer le code qui s’ouvre et ferme le Presse-papiers Windows.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Ces erreurs résultent de le `CMainView::OnInsertObject` gestionnaire. Traitement de la commande « Insérer un objet » est une autre zone où les choses ont changé un peu. Dans ce cas, il est plus facile de fusionner l’implémentation d’origine à celle offerte par AppWizard pour une nouvelle application de conteneur OLE. En fait, il s’agit d’une technique que vous pouvez appliquer pour le portage d’autres applications. Dans MFC/OLE1, vous avez affiché la boîte de dialogue « Insérer un objet » en appelant `AfxOleInsertDialog` (fonction). Dans cette version, vous construisez un `COleInsertObject` objet boîte de dialogue et appelez `DoModal`. En outre, les nouveaux éléments OLE sont créés avec un **CLSID** plutôt qu’une chaîne de nom de classe. Le résultat final doit ressembler à ceci

```cpp
COleInsertDialog dlg;
if (dlg.DoModal() != IDOK)
    return;

BeginWaitCursor();

CRectItem* pItem = NULL;
TRY
{
    // First create the C++ object
    pItem = GetDocument()->CreateItem();
    ASSERT_VALID(pItem);

    // Initialize the item from the dialog data.
    if (!dlg.CreateItem(pItem))
        AfxThrowMemoryException();
            // any exception will do
    ASSERT_VALID(pItem);

    // run the object if appropriate
    if (dlg.GetSelectionType() == COleInsertDialog::createNewItem)
        pItem->DoVerb(OLEIVERB_SHOW, this);

    // update right away
    pItem->UpdateLink();
    pItem->UpdateItemRectFromServer();

    // set selection to newly inserted item
    SetSelection(pItem);
    pItem->Invalidate();
}
CATCH (CException, e)
{
    // clean up item
    if (pItem != NULL)
        GetDocument()->DeleteItem(pItem);

    AfxMessageBox(IDP_FAILED_TO_CREATE);
}
END_CATCH

EndWaitCursor();
```

> [!NOTE]
> Insérer un nouvel objet peut être différent pour votre application) :

Il est également nécessaire d’inclure \<afxodlgs.h >, qui contient la déclaration pour la `COleInsertObject` classe de boîte de dialogue, ainsi que les autres boîtes de dialogue standard fournies par MFC.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Ces erreurs sont provoquées par le fait que certaines constantes OLE1 ont été modifiés dans OLE 2, bien que dans son concept, ils sont identiques. Dans ce cas `OLEVERB_PRIMARY` a changé à `OLEIVERB_PRIMARY`. Dans OLE1 et OLE 2, le verbe principal est généralement exécuté par un conteneur lorsque l’utilisateur double-clique sur un élément.

En outre, `DoVerb` accepte maintenant un paramètre supplémentaire : un pointeur vers une vue (`CView`*). Ce paramètre est uniquement utilisé pour implémenter des « Modification visuelle » (ou l’activation sur place). Pour l’instant vous définissez ce paramètre avec la valeur NULL, car vous n’implémentez pas cette fonctionnalité pour l’instant.

Pour vous assurer que le framework jamais in situ tente d’Active, vous devez substituer `COleClientItem::CanActivate` comme suit :

```cpp
BOOL CRectItem::CanActivate()
{
    return FALSE;
}
```

```Output
\oclient\rectitem.cpp(53) : error C2065: 'GetBounds' : undeclared identifier
\oclient\rectitem.cpp(53) : error C2064: term does not evaluate to a function
\oclient\rectitem.cpp(84) : error C2065: 'SetBounds' : undeclared identifier
\oclient\rectitem.cpp(84) : error C2064: term does not evaluate to a function
```

Dans MFC/OLE1, `COleClientItem::GetBounds` et `SetBounds` ont été utilisés pour interroger et manipuler l’étendue d’un élément (la `left` et `top` membres étaient toujours zéro). Dans MFC/OLE 2 Cela est plus directement pris en charge par `COleClientItem::GetExtent` et `SetExtent`, qui négocient avec un **taille** ou `CSize` à la place.

Le code de votre nouvelle SetItemRectToServer, et les appels UpdateItemRectFromServer ressembler à ceci :

```cpp
BOOL CRectItem::UpdateItemRectFromServer()
{
    ASSERT(m_bTrackServerSize);
    CSize size;
    if (!GetExtent(&size))
        return FALSE;    // blank

    // map from HIMETRIC to screen coordinates
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.LPtoDP(&size);
    }
    // just set the item size
    if (m_rect.Size() != size)
    {
        // invalidate the old size/position
        Invalidate();
        m_rect.right = m_rect.left + size.cx;
        m_rect.bottom = m_rect.top + size.cy;
        // as well as the new size/position
        Invalidate();
    }
    return TRUE;
}

BOOL CRectItem::SetItemRectToServer()
{
    // set the official bounds for the embedded item
    CSize size = m_rect.Size();
    {
        CClientDC screenDC(NULL);
        screenDC.SetMapMode(MM_HIMETRIC);
        screenDC.DPtoLP(&size);
    }
    TRY
    {
        SetExtent(size);    // may do a wait
    }
    CATCH(CException, e)
    {
        return FALSE;  // links will not allow SetBounds
    }
    END_CATCH
    return TRUE;
}
```

```Output
\oclient\frame.cpp(50) : error C2039: 'InWaitForRelease' : is not a member of 'COleClientItem'
\oclient\frame.cpp(50) : error C2065: 'InWaitForRelease' : undeclared identifier
\oclient\frame.cpp(50) : error C2064: term does not evaluate to a function
```

Dans l’API synchrone de MFC/OLE1 appels à partir d’un conteneur à un serveur ont été *simulé*, OLE1 étant intrinsèquement asynchrone dans de nombreux cas. Il était nécessaire de rechercher un appel asynchrone en attente en cours avant de traiter des commandes à partir de l’utilisateur. MFC/OLE1 fourni le `COleClientItem::InWaitForRelease` (fonction) pour effectuer cette opération. Dans MFC/OLE 2, cela n’est pas nécessaire, afin de pouvoir pour supprimer la substitution de OnCommand dans CMainFrame tous ensemble.

À ce stade OCLIENT sera compiler et lier.

## <a name="other-necessary-changes"></a>Autres modifications nécessaires

Voici quelques points qui ne sont pas effectués empêcher OCLIENT en cours d’exécution, toutefois. Il est préférable de résoudre ces problèmes maintenant, au lieu plus tard.

Tout d’abord, il est nécessaire initialiser les bibliothèques OLE. Cela est effectué en appelant `AfxOleInit` de `InitInstance`:

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

Il est également judicieux de vérifier les fonctions virtuelles pour les modifications de liste de paramètres. Une de ces fonctions est `COleClientItem::OnChange`substituée dans chaque application de conteneur MFC/OLE. En examinant l’aide en ligne, vous verrez qu’un « DWORD dwParam' supplémentaire a été ajouté. La nouvelle CRectItem::OnChange se présente comme suit :

```cpp
void
CRectItem::OnChange(OLE_NOTIFICATION wNotification, DWORD dwParam)
{
    if (m_bTrackServerSize && !UpdateItemRectFromServer())
    {
        // Blank object
        if (wNotification == OLE_CLOSED)
        {
            // no data received for the object - destroy it
            ASSERT(!IsVisible());
            GetDocument()->DeleteItem(this);
            return; // no update (item is gone now)
        }
    }
    if (wNotification != OLE_CLOSED)
        Dirty();
    Invalidate();
    // any change will cause a redraw
}
```

Dans MFC/OLE1, applications de conteneur dérivée de la classe de document à partir de `COleClientDoc`. Dans MFC/OLE 2 cette classe a été supprimée et remplacée par `COleDocument` (cette nouvelle organisation rend plus facile de créer des applications conteneur/serveur). Il existe un **#define** qui mappe `COleClientDoc` à `COleDocument` pour simplifier le portage d’applications MFC/OLE1 vers 2 MFC/OLE, par exemple OCLIENT. L’une des fonctionnalités non fournies par `COleDocument` qui a été fournie par `COleClientDoc` est le message de commande standard entrées de mappage. Cela est fait par les applications serveur, utilisent également `COleDocument` (indirectement), ne transmettent pas avec eux la surcharge de ces gestionnaires de commandes, sauf si elles sont une application conteneur/serveur. Vous devez ajouter les entrées suivantes à la table des messages CMainDoc :

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

L’implémentation de toutes ces commandes est en `COleDocument`, qui est la classe de base pour votre document.

À ce stade, OCLIENT est une application de conteneur OLE fonctionnelle. Il est possible d’insérer des éléments de tout type (OLE1 ou OLE 2). Étant donné que le code nécessaire pour permettre l’activation sur place n’est pas implémenté, la modification des éléments dans une fenêtre distincte, presque comme avec OLE1. La section suivante décrit les modifications nécessaires pour activer la modification sur place (parfois appelé « Modification visuelle »).

## <a name="adding-visual-editing"></a>Ajout de « Modification visuelle »

Une des fonctionnalités plus intéressantes d’OLE est l’activation sur place (ou « Modification visuelle »). Cette fonctionnalité permet à l’application serveur à tirer sur les parties de l’interface utilisateur du conteneur de fournir une interface de modification plus transparente pour l’utilisateur. Pour implémenter l’activation sur place à OCLIENT, certaines ressources spéciales doivent être ajoutés, ainsi que du code supplémentaire. Ces ressources et le code sont normalement fournis par AppWizard, en fait, une grande partie du code ici a été empruntée directement à partir d’une nouvelle application AppWizard avec prise en charge de « Conteneur ».

Tout d’abord, il est nécessaire d’ajouter une ressource de menu à utiliser lorsqu’il existe un élément qui est actif en place. Vous pouvez créer cette ressource de menu supplémentaires dans Visual C++ en copiant la ressource IDR_OCLITYPE et en supprimant tous sauf les fichier et fenêtre les fenêtres contextuelles. Deux barres de séparation sont insérés entre les fenêtres publicitaires intempestives de fichier et de fenêtre pour indiquer la séparation des groupes (il doit ressembler à : Fichier &#124; &#124; fenêtre). Pour plus d’informations sur ce que signifient ces séparateurs et comment les menus de serveur et un conteneur sont fusionnés consultez [Menus et ressources : Fusion de menus](../mfc/menus-and-resources-menu-merging.md).

Une fois que vous avez ces menus créés, vous devez informer l’infrastructure à leur sujet. Cela est effectué en appelant `CDocTemplate::SetContainerInfo` du modèle de document avant de l’ajouter à la liste de modèle de document dans votre InitInstance. Le nouveau code pour enregistrer le modèle de document ressemble à ceci :

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

La ressource IDR_OLECLITYPE_INPLACE est la ressource in situ spéciale créée dans Visual C++.

Pour activer l’activation sur place, il existe certaines choses pour modifier à la fois dans le `CView` (CMainView) de classe dérivée, ainsi que les `COleClientItem` (CRectItem) de classe dérivée. Toutes ces substitutions sont fournis par AppWizard, et la majeure partie de l’implémentation proviendra directement à partir d’une application de AppWizard par défaut.

Dans la première étape de ce port, l’activation sur place a été désactivée entièrement en substituant `COleClientItem::CanActivate`. Cette substitution doit être supprimée pour permettre l’activation sur place. En outre, NULL a été transmise à tous les appels à `DoVerb` (il existe deux d'entre eux) étant donné que fournit la vue était nécessaire uniquement pour l’activation sur place. Pour implémenter entièrement l’activation sur place, il est nécessaire de transmettre la bonne vue dans le `DoVerb` appeler. Un de ces appels est dans `CMainView::OnInsertObject`:

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

C’est `CMainView::OnLButtonDblClk`:

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Il est nécessaire de remplacer `COleClientItem::OnGetItemPosition`. Cela indique au serveur où placer sa fenêtre par rapport à la fenêtre du conteneur lorsque l’élément est activé sur place. Pour OCLIENT, l’implémentation est simple :

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

La plupart des serveurs également implémenter ce que l'on appelle « redimensionnement en place. » Ainsi, la fenêtre du serveur être dimensionné et déplacé alors que l’utilisateur modifie l’élément. Le conteneur doit participer à cette action, car déplacez ou redimensionnez la fenêtre généralement affecte la position et la taille du document conteneur lui-même. L’implémentation pour OCLIENT synchronise le rectangle interne maintenu par m_rect avec la nouvelle position et la taille.

```cpp
BOOL CRectItem::OnChangeItemPosition(const CRect& rectPos)
{
    ASSERT_VALID(this);

    if (!COleClientItem::OnChangeItemPosition(rectPos))
        return FALSE;

    Invalidate();
    m_rect = rectPos;
    Invalidate();
    GetDocument()->SetModifiedFlag();

    return TRUE;
}
```

À ce stade, il est assez de code pour autoriser un élément doit être activé sur place et traitent de dimensionnement et de déplacement de l’élément quand il est actif, mais aucun code ne permet à l’utilisateur quitter la session d’édition. Bien que certains serveurs offrent cette fonctionnalité eux-mêmes en gérant la touche ÉCHAP, il est recommandé que les conteneurs fournissent deux façons de désactiver un élément : (1) en cliquant sur hors de l’élément, (2) en appuyant sur la touche ÉCHAP.

Pour la touche ÉCHAP, ajoutez un accélérateur avec Visual C++ qui mappe la clé VK_ESCAPE à une commande, ID_CANCEL_EDIT est ajoutée aux ressources. Le gestionnaire pour cette commande suit :

```cpp
// The following command handler provides the standard
// keyboard user interface to cancel an in-place
// editing session.void CMainView::OnCancelEdit()
{
    // Close any in-place active item on this view.
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->Close();
    ASSERT(GetDocument()->GetInPlaceActiveItem(this) == NULL);
}
```

Pour gérer le cas où l’utilisateur clique en dehors de l’élément, vous ajoutez le code suivant au début de `CMainView::SetSelection`:

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Lorsqu’un élément est actif en place, il doit avoir le focus. Pour vous assurer que c’est le cas, vous gérez OnSetFocus afin que le focus est toujours transféré à l’élément actif lorsque votre vue reçoit le focus :

```cpp
// Special handling of OnSetFocus and OnSize are required
// when an object is being edited in-place.
void CMainView::OnSetFocus(CWnd* pOldWnd)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);

    if (pActiveItem != NULL &&
        pActiveItem->GetItemState() == COleClientItem::activeUIState)
    {
        // need to set focus to this item if it is same view
        CWnd* pWnd = pActiveItem->GetInPlaceWindow();
        if (pWnd != NULL)
        {
            pWnd->SetFocus();   // don't call the base class
            return;
        }
    }

    CView::OnSetFocus(pOldWnd);
}
```

Lorsque la vue est redimensionnée, vous devez notifier l’élément active le rectangle de découpage a changé. Pour cela vous fournissez un gestionnaire pour `OnSize`:

```cpp
void CMainView::OnSize(UINT nType, int cx, int cy)
{
    CView::OnSize(nType, cx, cy);
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL)
        pActiveItem->SetItemRects();
}
```

## <a name="case-study-hiersvr-from-mfc-20"></a>Étude de cas : HIERSVR à partir de MFC 2.0

[HIERSVR](../overview/visual-cpp-samples.md) a également été incluse dans MFC 2.0 et implémenté OLE avec MFC/OLE1. Cette note décrit brièvement les étapes auxquelles cette application a été initialement convertie pour utiliser les classes MFC/OLE 2. Un certain nombre de fonctionnalités ont été ajouté après que le port initial a été effectué pour mieux illustrer les classes MFC/OLE 2. Ces fonctionnalités ne sont pas couverts ici ; reportez-vous à l’exemple lui-même pour plus d’informations sur ces fonctionnalités avancées.

> [!NOTE]
> Les erreurs du compilateur et le processus pas à pas a été créé avec Visual C++ 2.0. Emplacements et messages d’erreur spécifiques peuvent ont été modifiés avec Visual C++ 4.0, mais les informations conceptuelles restent valides.

## <a name="getting-it-up-and-running"></a>Il route

L’approche adoptée pour le port de l’exemple HIERSVR vers MFC/OLE doit commencer par créer et de résolution des erreurs du compilateur évident qui entraîneront. Si vous prenez l’exemple de HIERSVR à partir de MFC 2.0 et compilez sous cette version de MFC, vous trouverez qu’il n’existe pas de nombreuses erreurs pour résoudre (bien qu’il existe plusieurs avec l’exemple OCLIENT). Les erreurs dans l’ordre dans lequel ils se produisent généralement sont décrits ci-dessous.

## <a name="compile-and-fix-errors"></a>Compilation et correction des erreurs

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Cette première erreur signale un problème beaucoup plus important avec la `InitInstance` (fonction) pour les serveurs. L’initialisation nécessaire pour un serveur OLE est probablement un des plus grands changements, que vous devrez apporter à votre application MFC/OLE1 pour pouvoir l’exécuter. La meilleure chose à faire est d’examiner ce qui crée par AppWizard pour un serveur OLE et de modifier votre code si nécessaire. Voici quelques points à prendre en compte :

Il est nécessaire d’initialiser les bibliothèques OLE en appelant `AfxOleInit`

Appelez SetServerInfo sur l’objet de modèle de document pour définir les descripteurs de ressources de serveur et les informations de classe runtime que vous ne pouvez pas définir avec le `CDocTemplate` constructeur.

Ne pas d’afficher la fenêtre principale de votre application si /Embedding figure sur la ligne de commande.

Vous aurez besoin d’un **GUID** pour votre document. Il s’agit d’un identificateur unique pour votre type de document (128 bits). AppWizard créera un pour vous, donc, si vous utilisez la technique décrite ici consistant à copier le nouveau code à partir d’une nouvelle application de serveur générée par AppWizard, vous pouvez simplement « volez » le GUID à partir de cette application. Si ce n’est pas le cas, vous pouvez utiliser le GUIDGEN. Utilitaire EXE dans le répertoire BIN.

Il est nécessaire de « se connecter » votre `COleTemplateServer` objet pour le modèle de document en appelant `COleTemplateServer::ConnectTemplate`.

Mettre à jour le Registre système lorsque votre application est exécutée en mode autonome. Ainsi, si l’utilisateur déplace le. EXE pour votre application, exécuter à partir de son nouvel emplacement met à jour la base de données de l’inscription du système Windows pour qu’il pointe vers le nouvel emplacement.

Après avoir appliqué toutes ces modifications en fonction de ce qui crée par AppWizard pour `InitInstance`, la `InitInstance` (et GUID) pour HIERSVR doit se présenter comme suit :

```cpp
// this is the GUID for HIERSVR documents
static const GUID BASED_CODE clsid =
{ 0xA0A16360L, 0xC19B, 0x101A, { 0x8C, 0xE5, 0x00, 0xDD, 0x01, 0x11, 0x3F, 0x12 } };

/////////////////////////////////////////////////////////////////////////////
// COLEServerApp initialization

BOOL COLEServerApp::InitInstance()
{
    // OLE 2 initialization
    if (!AfxOleInit())
    {
        AfxMessageBox("Initialization of the OLE failed!");
        return FALSE;
    }

    // Standard initialization
    LoadStdProfileSettings();   // Load standard INI file options

    // Register document templates
    CDocTemplate* pDocTemplate;
    pDocTemplate = new CMultiDocTemplate(IDR_HIERSVRTYPE,
        RUNTIME_CLASS(CServerDoc),
        RUNTIME_CLASS(CMDIChildWnd),
        RUNTIME_CLASS(CServerView));
    pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB);
    AddDocTemplate(pDocTemplate);

    // create main MDI Frame window
    CMainFrame* pMainFrame = new CMainFrame;
    if (!pMainFrame->LoadFrame(IDR_MAINFRAME))
        return FALSE;
    m_pMainWnd = pMainFrame;

    SetDialogBkColor(); // gray look

    // enable file manager drag/drop and DDE Execute open
    m_pMainWnd->DragAcceptFiles();
    EnableShellOpen();

    m_server.ConnectTemplate(clsid, pDocTemplate, FALSE);
    COleTemplateServer::RegisterAll();

    // try to launch as an OLE server
    if (RunEmbedded())
    {
        // "short-circuit" initialization -- run as server!
        return TRUE;
    }
    m_server.UpdateRegistry();
    RegisterShellFileTypes();

    // not run as OLE server, so show the main window
    if (m_lpCmdLine[0] == '\0')
    {
        // create a new (empty) document
        OnFileNew();
    }
    else
    {
        // open an existing document
        OpenDocumentFile(m_lpCmdLine);
    }

    pMainFrame->ShowWindow(m_nCmdShow);
    pMainFrame->UpdateWindow();

    return TRUE;
}
```

Vous remarquerez que le code ci-dessus fait référence à un nouvel ID de ressource, IDR_HIERSVRTYPE_SRVR_EMB. Il s’agit de la ressource de menu à utiliser lors de la modification d’un document qui est incorporé dans un autre conteneur. Dans MFC/OLE1, les éléments de menu spécifiques à l’édition d’un élément incorporé ont été modifiés à la volée. À l’aide d’une structure de menu entièrement différent lors de la modification d’un élément incorporé au lieu de modifier un document basé sur le fichier rend beaucoup plus facile de fournir différentes interfaces utilisateur pour ces deux modes distincts. Comme vous le verrez plus tard, une ressource de menu entièrement distinct est utilisée lors de la modification d’une objet incorporé sur place.

Pour créer cette ressource, charger le script de ressources dans Visual C++ et copier la ressource de menu IDR_HIERSVRTYPE existante. Renommez la nouvelle ressource IDR_HIERSVRTYPE_SRVR_EMB (il s’agit de la même convention d’affectation de noms par AppWizard). Ensuite modifier l’option « Enregistrer » pour « Mise à jour de fichier ; » Attribuez-lui ID_FILE_UPDATE d’ID de commande. Modifiez également « Fichier Enregistrer sous » pour « Fichier Enregistrer copie sous » ; Attribuez-lui ID_FILE_SAVE_COPY_AS d’ID de commande. Le framework fournit l’implémentation de ces deux commandes.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Il existe un nombre d’erreurs résultant de la substitution de `OnSetData`, car il fait référence à la **OLESTATUS** type. **OLESTATUS** a été la façon OLE1 renvoyé des erreurs. Ce problème est devenu **HRESULT** dans OLE 2, bien que MFC convertit généralement un **HRESULT** dans un `COleException` contenant l’erreur. Dans ce cas particulier, la substitution de `OnSetData` n’est plus nécessaire, donc la plus simple consiste à supprimer.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

Le `COleServerItem` constructeur prend un paramètre de 'BOOL' supplémentaire. Cet indicateur détermine comment la gestion de la mémoire est effectuée sur le `COleServerItem` objets. En lui affectant la valeur True, le framework gère la gestion de la mémoire de ces objets, leur suppression lorsqu’ils ne sont plus nécessaires. HIERSVR utilise `CServerItem` (dérivée de `COleServerItem`) objets dans le cadre de ses données natives, donc vous devez définir cet indicateur sur FALSE. HIERSVR ainsi déterminer lorsque chaque élément de serveur est supprimé.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Comme l’indiquent, ces erreurs, il existe certaines fonctions 'pure virtual' qui n’ont pas été substituées dans CServerItem. Cela est très probablement dû au fait que liste de paramètres de la fonction membre OnDraw a changé. Pour corriger cette erreur, modifiez `CServerItem::OnDraw` comme suit (ainsi que la déclaration dans svritem.h) :

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

Le nouveau paramètre est « rSize ». Ainsi, vous permettant d’entrer dans la taille du dessin, si elle est pratique. Cette taille doit être dans **HIMETRIC**. Dans ce cas, il n’est pas pratique remplir cette valeur, le framework appelle `OnGetExtent` pour récupérer l’étendue. Pour que cela fonctionne, vous devrez implémenter `OnGetExtent`:

```cpp
BOOL CServerItem::OnGetExtent(DVASPECT dwDrawAspect, CSize& rSize)
{
    if (dwDrawAspect != DVASPECT_CONTENT)
        return COleServerItem::OnGetExtent(dwDrawAspect, rSize);

    rSize = CalcNodeSize();
    return TRUE;
}
```

```Output
\hiersvr\svritem.cpp(104) : error C2065: 'm_rectBounds' : undeclared identifier
\hiersvr\svritem.cpp(104) : error C2228: left of '.SetRect' must have class/struct/union type
\hiersvr\svritem.cpp(106) : error C2664: 'void __pascal __far DPtoLP(struct ::tagPOINT __far *,
    int)__far const ' : cannot convert parameter 1 from 'int __far *' to 'struct ::tagPOINT __far *'
```

Dans la fonction CServerItem::CalcNodeSize la taille de l’élément est convertie en **HIMETRIC** et stockée dans *m_rectBounds*. La non documentée '*m_rectBounds*' membre de `COleServerItem` n’existe pas (elle a été partiellement remplacée par *m_sizeExtent*, mais dans OLE 2 ce membre a une utilisation légèrement plus *m_rectBounds* dans OLE1). Au lieu de définir la **HIMETRIC** taille dans cette variable de membre, vous allez renvoyer. Cette valeur de retour est utilisée dans `OnGetExtent`, implémentée précédemment.

```cpp
CSize CServerItem::CalcNodeSize()
{
    CClientDC dcScreen(NULL);

    m_sizeNode = dcScreen.GetTextExtent(m_strDescription,
        m_strDescription.GetLength());
    m_sizeNode += CSize(CX_INSET * 2, CY_INSET * 2);

    // set suggested HIMETRIC size
    CSize size(m_sizeNode.cx, m_sizeNode.cy);
    dcScreen.SetMapMode(MM_HIMETRIC);
    dcScreen.DPtoLP(&size);
    return size;
}
```

CServerItem substitue également `COleServerItem::OnGetTextData`. Cette fonction est obsolète dans MFC/OLE et est remplacée par un autre mécanisme. La version 3.0 de MFC de l’exemple OLE MFC [HIERSVR](../overview/visual-cpp-samples.md) implémente cette fonctionnalité en substituant `COleServerItem::OnRenderFileData`. Cette fonctionnalité n’est pas importante pour ce port de base, afin de pouvoir supprimer le remplacement de OnGetTextData.

Il existe de nombreuses erreurs dans svritem.cpp qui n’ont pas été traités. Ils ne sont pas des erreurs « réelles » — simplement les erreurs provoquées par les erreurs précédentes.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` prend en charge n’est plus le `bIncludeNative` indicateur. Les données natives (les données écrites par la fonction de sérialisation de l’élément du serveur) sont toujours copiées, afin de supprimer le premier paramètre. En outre, `CopyToClipboard` lève une exception quand une erreur se produit au lieu de retourner la valeur FALSE. Modifiez le code pour CServerView::OnEditCopy comme suit :

```cpp
void CServerView::OnEditCopy()
{
    if (m_pSelectedNode == NULL)
        AfxThrowNotSupportedException();

    TRY
    {
        m_pSelectedNode->CopyToClipboard(TRUE);
    }
    CATCH_ALL(e)
    {
        AfxMessageBox("Copy to clipboard failed");
    }
    END_CATCH_ALL
}
```

Bien que vous rencontrez des erreurs plus résultant de la compilation de la version 2.0 de MFC de HIERSVR qu’il avait pour la même version de OCLIENT, se sont réellement moins modifications.

À ce stade HIERSVR compiler et lier et fonctionner comme serveur OLE, mais sans la fonction d’édition sur place, ce qui sera implémentée ensuite.

## <a name="adding-visual-editing"></a>Ajout de « Modification visuelle »

Pour ajouter « Modification visuelle » (ou l’activation sur place) à cette application server, il existe seulement quelques éléments, de que vous devez prendre soin :

- Vous avez besoin d’une ressource de menu spécial à utiliser lors de l’élément est actif en place.

- Cette application a une barre d’outils, et vous devrez donc une barre d’outils avec uniquement un sous-ensemble de la barre d’outils normal pour faire correspondre les commandes de menu disponibles à partir du serveur (correspond à la ressource de menu mentionnée ci-dessus).

- Vous avez besoin d’une nouvelle classe dérivée de `COleIPFrameWnd` qui fournit l’interface utilisateur sur place (comme vous transmettriez CMainFrame, dérivée de `CMDIFrameWnd`, fournit l’interface utilisateur MDI).

- Vous devez indiquer à l’infrastructure sur ces ressources spéciales et les classes.

La ressource de menu est facile de créer. Exécutez Visual C++, copier la ressource de menu IDR_HIERSVRTYPE vers une ressource de menu appelée IDR_HIERSVRTYPE_SRVR_IP. Modifier le menu afin qu’uniquement les modification et aide menus déroulants sont conservés. Ajouter deux séparateurs au menu entre les menus aide et de modification (il doit ressembler à : Modifier &#124; &#124; aider). Pour plus d’informations sur ce que signifient ces séparateurs et comment les menus de serveur et un conteneur sont fusionnés, consultez [Menus et ressources : Fusion de menus](../mfc/menus-and-resources-menu-merging.md).

L’image bitmap de la barre d’outils du sous-ensemble peut être facilement créée en copiant celui à partir d’une application générée par AppWizard fraîche avec une option « Serveur » activée. Cette image bitmap ne peut ensuite être importée dans Visual C++. Veillez à donner à l’image bitmap à un ID de IDR_HIERSVRTYPE_SRVR_IP.

La classe dérivée de `COleIPFrameWnd` peuvent être copiés à partir d’une application générée par AppWizard avec prise en charge de serveur. Copiez les deux fichiers, IPFRAME. CPP et IPFRAME. H et ajoutez-les au projet. Assurez-vous que le `LoadBitmap` appel fait référence à IDR_HIERSVRTYPE_SRVR_IP, l’image bitmap créé à l’étape précédente.

Maintenant que les nouvelles ressources et les classes sont créés, ajoutez le code nécessaire pour que le framework sait sur ces (et sait que maintenant cette application prend en charge la modification sur place). Cela s’effectue en ajoutant des paramètres plus à la `SetServerInfo` appeler dans le `InitInstance` (fonction) :

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Il est maintenant prêt à exécuter sur place dans n’importe quel conteneur qui prend également en charge l’activation sur place. Cependant, il existe un bogue mineur traînent dans le code. HIERSVR prend en charge un menu contextuel, affiché lorsque l’utilisateur appuie sur le bouton droit de la souris. Ce menu fonctionne lorsque HIERSVR est entièrement ouvert, mais ne fonctionne pas lorsque vous modifiez une incorporation dans sur place. La raison peut être épinglée à cette seule ligne de code dans CServerView::OnRButtonDown :

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Notez que la référence à `AfxGetApp()->m_pMainWnd`. Lorsque le serveur est activé sur place, il possède une fenêtre principale et m_pMainWnd est définie, mais il est généralement invisible. En outre, cette fenêtre fait référence à la *principal* fenêtre de l’application, la fenêtre frame MDI qui s’affiche lorsque le serveur est entièrement ouvrir ou exécuté en mode autonome. Il ne fait pas référence à la fenêtre frame actif, qui lorsqu’in situ activé est un cadre de fenêtre dérivées de `COleIPFrameWnd`. Pour obtenir la fenêtre active correcte même lorsque la modification sur place, cette version de MFC ajoute une nouvelle fonction, `AfxGetMainWnd`. En règle générale, vous devez utiliser cette fonction au lieu de `AfxGetApp()->m_pMainWnd`. Ce code doit modifier comme suit :

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Vous disposez maintenant d’un serveur OLE minimale activé pour l’activation sur place fonctionnelle. Mais il existe toujours des nombreuses fonctionnalités disponibles avec MFC/OLE 2 qui n’étaient pas disponibles dans MFC/OLE1. Consultez l’exemple HIERSVR pour plus d’informations sur les fonctionnalités que vous pouvez souhaiter implémenter. Certaines des fonctionnalités qui implémente HIERSVR sont répertoriés ci-dessous :

- Le zoom pour le comportement de WYSIWYG vrai en ce qui concerne le conteneur.

- Glisser / déposer et un format de Presse-papiers personnalisés.

- Le défilement de la fenêtre du conteneur en tant que la sélection est modifié.

L’exemple HIERSVR dans MFC 3.0 utilise également un design légèrement différent pour ses éléments de serveur. Cela permet d’économiser la mémoire et rend vos liens plus flexible. Avec la version 2.0 de HIERSVR chaque nœud dans l’arborescence *est un* `COleServerItem`. `COleServerItem` exécute un peu de surcharge est strictement nécessaire pour chacun de ces nœuds, mais un `COleServerItem` est requis pour chaque lien actif. Mais la plupart du temps, il existe très peu de liens actifs à un moment donné. Pour rendre plus efficace, HIERSVR dans cette version de MFC sépare le nœud à partir de la `COleServerItem`. Il possède les deux un CServerNode et un `CServerItem` classe. Le `CServerItem` (dérivée de `COleServerItem`) est créé uniquement si nécessaire. Une fois que le conteneur (ou conteneurs) cesser d’utiliser ce lien particulier pour ce nœud spécifique, l’objet CServerItem associé à la CServerNode est supprimé. Cette conception est plus efficace et plus flexible. Sa flexibilité lors du traitement de plusieurs liens de sélection. Aucune de ces deux versions de HIERSVR ne prennent en charge la sélection multiple, mais il serait beaucoup plus facile à ajouter (pour prendre en charge des liens vers ces sélections) avec la version 3.0 de MFC de HIERSVR, dans la mesure où le `COleServerItem` est séparé des données natives.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

---
description: 'En savoir plus sur : TN041 : migration de MFC/OLE1 vers MFC/OLE 2'
title: 'TN041 : migration de MFC-OLE1 vers MFC-OLE 2'
ms.date: 10/18/2018
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
ms.openlocfilehash: 83bb9869d61ca9d2c92780fc6bed55ce3c3ff798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215376"
---
# <a name="tn041-mfcole1-migration-to-mfcole-2"></a>TN041 : migration de MFC/OLE1 vers MFC/OLE 2

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

## <a name="general-issues-relating-to-migration"></a>Problèmes généraux liés à la migration

L’un des objectifs de conception des classes OLE 2 dans MFC 2,5 (et versions ultérieures) consistait à conserver une grande partie de la même architecture mise en place dans MFC 2,0 pour la prise en charge d’OLE 1,0. En conséquence, la plupart des classes OLE de MFC 2,0 existent toujours dans cette version de MFC ( `COleDocument` , `COleServerDoc` , `COleClientItem` , `COleServerItem` ). De plus, la plupart des API de ces classes sont exactement les mêmes. Toutefois, OLE 2 est radicalement différent d’OLE 1,0 et vous pouvez vous attendre à ce que certains détails aient été modifiés. Si vous êtes familiarisé avec la prise en charge de OLE1 de MFC 2.0, vous vous sentirez à l’aise avec la prise en charge 2,0 de MFC.

Si vous prenez une application MFC/OLE1 existante et y ajoutez des fonctionnalités OLE 2, vous devez d’abord lire cette note. Cette note aborde certains problèmes généraux que vous pouvez rencontrer lors du Portage de vos fonctionnalités OLE1 vers MFC/OLE 2, puis décrit les problèmes découverts lors du Portage de deux applications incluses dans MFC 2,0 : les exemples OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md).

## <a name="mfc-documentview-architecture-is-important"></a>L’architecture document/vue MFC est importante

Si votre application n’utilise pas l’architecture document/vue de MFC et que vous souhaitez ajouter la prise en charge OLE 2 à votre application, il est temps de passer au document ou à la vue. Un grand nombre des avantages des classes OLE 2 de MFC ne sont réalisés que lorsque votre application utilise l’architecture et les composants intégrés de MFC.

L’implémentation d’un serveur ou d’un conteneur sans utiliser l’architecture MFC est possible, mais n’est pas recommandée.

## <a name="use-mfc-implementation-instead-of-your-own"></a>Utilisez l’implémentation MFC à la place de la vôtre

Les classes MFC « implémentation intégrée » telles que `CToolBar` , `CStatusBar` et `CScrollView` ont un code de cas spécial intégré pour la prise en charge OLE 2. Par conséquent, si vous pouvez utiliser ces classes dans votre application, vous tirerez parti de l’effort qui leur est présenté pour les rendre compatibles OLE. Là encore, il est possible de « déployer vos propres classes » ici à ces fins, mais cela n’est pas suggéré. Si vous avez besoin d’implémenter des fonctionnalités similaires, le code source MFC constitue une excellente référence pour traiter certains des points plus fins d’OLE (surtout lorsqu’il s’agit d’une activation sur place).

## <a name="examine-the-mfc-sample-code"></a>Examiner l’exemple de code MFC

Il existe un certain nombre d’exemples MFC qui incluent la fonctionnalité OLE. Chacune de ces applications implémente OLE à partir d’un angle différent :

- [HIERSVR](../overview/visual-cpp-samples.md) Conçu principalement pour une utilisation en tant qu’application serveur. Elle a été incluse dans MFC 2,0 en tant qu’application MFC/OLE1 et a été reportée vers MFC/OLE 2, puis étendue de sorte qu’elle implémente de nombreuses fonctionnalités OLE disponibles dans OLE 2.

- [OCLIENT](../overview/visual-cpp-samples.md) Il s’agit d’une application de conteneur autonome, conçue pour illustrer la plupart des fonctionnalités OLE du point de vue d’un conteneur. Elle a également été reportée à partir de MFC 2,0, puis étendue pour prendre en charge la plupart des fonctionnalités OLE plus avancées, telles que les formats de presse-papiers personnalisés et les liens vers les éléments incorporés.

- [DRAWCLI](../overview/visual-cpp-samples.md) Cette application implémente la prise en charge des conteneurs OLE comme OCLIENT le fait, sauf qu’elle le fait dans le cadre d’un programme de dessin orienté objet existant. Il vous montre comment vous pouvez implémenter la prise en charge des conteneurs OLE et l’intégrer à votre application existante.

- [SUPERPAD](../overview/visual-cpp-samples.md) Cette application, ainsi qu’une application fine autonome, est également un serveur OLE. La prise en charge de serveur qu’elle implémente est relativement minimaliste. Il est particulièrement intéressant de savoir comment il utilise les services du presse-papiers OLE pour copier des données vers le presse-papiers, mais utilise les fonctionnalités intégrées au contrôle Windows « Edit » pour implémenter la fonctionnalité de collage du presse-papiers. Il s’agit d’une combinaison intéressante d’utilisation des API Windows traditionnelles, ainsi que de l’intégration avec les nouvelles API OLE.

Pour plus d’informations sur les exemples d’applications, consultez l' « aide de l’exemple MFC ».

## <a name="case-study-oclient-from-mfc-20"></a>Étude de cas : OCLIENT de MFC 2,0

Comme indiqué ci-dessus, [OCLIENT](../overview/visual-cpp-samples.md) était inclus dans MFC 2,0 et implémenté OLE avec MFC/OLE1. Les étapes par lesquelles cette application a été initialement convertie pour utiliser les classes MFC/OLE 2 sont décrites ci-dessous. Un certain nombre de fonctionnalités ont été ajoutées après la fin du port initial pour mieux illustrer les classes MFC/OLE. Ces fonctionnalités ne seront pas couvertes ici. Pour plus d’informations sur ces fonctionnalités avancées, reportez-vous à l’exemple lui-même.

> [!NOTE]
> Les erreurs du compilateur et le processus pas à pas ont été créés avec Visual C++ 2,0. Des messages d’erreur et des emplacements spécifiques ont peut-être été modifiés avec Visual C++ 4,0, mais les informations conceptuelles restent valides.

### <a name="getting-it-up-and-running"></a>Mise en service

L’approche adoptée pour porter l’exemple OCLIENT vers MFC/OLE consiste à commencer par le générer et à résoudre les erreurs de compilateur évidentes qui en résultent. Si vous prenez l’exemple OCLIENT de MFC 2,0 et le compilez sous cette version de MFC, vous constaterez qu’il n’existe pas de nombreuses erreurs à résoudre. Les erreurs dans l’ordre dans lequel elles se sont produites sont décrites ci-dessous.

### <a name="compile-and-fix-errors"></a>Compiler et corriger les erreurs

```Output
\oclient\mainview.cpp(104) : error C2660: 'Draw' : function does not take 4 parameters
```

Les premières préoccupations en matière d’erreur `COleClientItem::Draw` . Dans MFC/OLE1, il a fallu plus de paramètres que la version de MFC/OLE. Les paramètres supplémentaires n’étaient souvent pas nécessaires et généralement NULL (comme dans cet exemple). Cette version de MFC peut déterminer automatiquement les valeurs de lpWBounds lorsque le CDC qui est dessiné est un contrôleur de périphérique de métafichier. En outre, le paramètre pFormatDC n’est plus nécessaire, car le Framework en génère un à partir du « attribut DC » du contrôleur de domaine principal passé. Pour résoudre ce problème, il vous suffit de supprimer les deux paramètres NULL supplémentaires pour l’appel de dessin.

```Output
\oclient\mainview.cpp(273) : error C2065: 'OLE_MAXNAMESIZE' : undeclared identifier
\oclient\mainview.cpp(273) : error C2057: expected constant expression
\oclient\mainview.cpp(280) : error C2664: 'CreateLinkFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(286) : error C2664: 'CreateFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
\oclient\mainview.cpp(288) : error C2664: 'CreateStaticFromClipboard' : cannot convert parameter 1 from 'char [1]' to 'enum ::tagOLERENDER '
```

Les erreurs ci-dessus résultent du fait que toutes les `COleClientItem::CreateXXXX` fonctions dans MFC/OLE1 nécessitaient la transmission d’un nom unique pour représenter l’élément. Il s’agissait d’une exigence de l’API OLE sous-jacente. Cela n’est pas nécessaire dans MFC/OLE 2, car OLE 2 n’utilise pas DDE comme mécanisme de communication sous-jacent (le nom a été utilisé dans les conversations DDE). Pour résoudre ce problème, vous pouvez supprimer la `CreateNewName` fonction ainsi que toutes les références à celle-ci. Il est facile de savoir ce que chaque fonction MFC/OLE attend dans cette version en plaçant simplement votre curseur sur l’appel et en appuyant sur F1.

Une autre zone très différente est la gestion du presse-papiers OLE 2. Avec OLE1, vous avez utilisé les API du presse-papiers Windows interagir avec le presse-papiers. Avec OLE 2, cette opération s’effectue à l’aide d’un mécanisme différent. Les API MFC/OLE1 supposaient que le presse-papiers était ouvert avant de copier un `COleClientItem` objet dans le presse-papiers. Cela n’est plus nécessaire et entraîne l’échec de toutes les opérations du presse-papiers MFC/OLE. Lorsque vous modifiez le code pour supprimer les dépendances sur `CreateNewName` , vous devez également supprimer le code qui s’ouvre et ferme le presse-papiers Windows.

```Output
\oclient\mainview.cpp(332) : error C2065: 'AfxOleInsertDialog' : undeclared identifier
\oclient\mainview.cpp(332) : error C2064: term does not evaluate to a function
\oclient\mainview.cpp(344) : error C2057: expected constant expression
\oclient\mainview.cpp(347) : error C2039: 'CreateNewObject' : is not a member of 'CRectItem'
```

Ces erreurs proviennent du `CMainView::OnInsertObject` Gestionnaire. La gestion de la commande « INSERT New Object » est une autre zone où les choses ont changé de manière très simple. Dans ce cas, il est plus facile de fusionner simplement l’implémentation d’origine avec celle fournie par AppWizard pour une nouvelle application de conteneur OLE. En fait, il s’agit d’une technique que vous pouvez appliquer au portage d’autres applications. Dans MFC/OLE1, vous avez affiché la boîte de dialogue « Insérer un objet » en appelant la `AfxOleInsertDialog` fonction. Dans cette version, vous construisez un `COleInsertObject` objet de boîte de dialogue et appelez `DoModal` . En outre, les nouveaux éléments OLE sont créés avec un **CLSID** au lieu d’une chaîne ClassName. Le résultat final doit ressembler à ce qui suit

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
> L’insertion d’un nouvel objet peut être différente pour votre application) :

Il est également nécessaire d’inclure \<afxodlgs.h> , qui contient la déclaration pour la `COleInsertObject` classe Dialog, ainsi que les autres boîtes de dialogue standard fournies par MFC.

```Output
\oclient\mainview.cpp(367) : error C2065: 'OLEVERB_PRIMARY' : undeclared identifier
\oclient\mainview.cpp(367) : error C2660: 'DoVerb' : function does not take 1 parameters
```

Ces erreurs sont dues au fait que certaines constantes OLE1 ont été modifiées dans OLE 2, même si leur concept est identique. Dans ce cas, `OLEVERB_PRIMARY` est passé à `OLEIVERB_PRIMARY` . Dans OLE1 et OLE 2, le verbe principal est généralement exécuté par un conteneur lorsque l’utilisateur double-clique sur un élément.

En outre, `DoVerb` prend désormais un paramètre supplémentaire, un pointeur vers une vue ( `CView` *). Ce paramètre est utilisé uniquement pour implémenter la « modification visuelle » (ou l’activation sur place). Pour le moment, vous affectez à ce paramètre la valeur NULL, car vous n’implémentez pas cette fonctionnalité pour l’instant.

Pour vous assurer que l’infrastructure ne tente jamais l’activation sur place, vous devez remplacer `COleClientItem::CanActivate` comme suit :

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

Dans MFC/OLE1, `COleClientItem::GetBounds` et `SetBounds` ont été utilisés pour interroger et manipuler l’étendue d’un élément (les `left` `top` membres et étaient toujours nuls). Dans MFC/OLE 2, cela est plus directement pris en charge par `COleClientItem::GetExtent` et `SetExtent` , qui traitent une **taille** ou à la `CSize` place.

Le code de vos nouveaux appels SetItemRectToServer et UpdateItemRectFromServer ressemble à ceci :

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

Dans les appels de l’API synchrone MFC/OLE1 à partir d’un conteneur vers un serveur, la *simulation* de OLE1 était fondamentalement asynchrone dans de nombreux cas. Il était nécessaire de vérifier si un appel asynchrone en attente était en cours avant de traiter des commandes de l’utilisateur. MFC/OLE1 offrait la `COleClientItem::InWaitForRelease` fonction permettant de le faire. Dans MFC/OLE 2, ce n’est pas nécessaire. vous pouvez donc supprimer le remplacement de OnCommand dans CMainFrame.

À ce stade, OCLIENT effectuera la compilation et la liaison.

### <a name="other-necessary-changes"></a>Autres modifications nécessaires

Il y a peu d’éléments qui ne sont pas exécutés, mais qui empêchent l’exécution d’OCLIENT. Il est préférable de corriger ces problèmes maintenant plutôt que plus tard.

Tout d’abord, il est nécessaire d’initialiser les bibliothèques OLE. Pour ce faire, appelez `AfxOleInit` à partir de `InitInstance` :

```cpp
if (!AfxOleInit())
{
    AfxMessageBox("Failed to initialize OLE libraries");
    return FALSE;
}
```

Il est également judicieux de vérifier les fonctions virtuelles pour les modifications de liste de paramètres. Une telle fonction est `COleClientItem::OnChange` , remplacée dans chaque application de conteneur MFC/OLE. En regardant l’aide en ligne, vous verrez qu’un « DWORD dwParam » supplémentaire a été ajouté. Le nouvel CRectItem :: OnChange se présente comme suit :

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

Dans MFC/OLE1, les applications de conteneur dérivent la classe de document de `COleClientDoc` . Dans MFC/OLE 2, cette classe a été supprimée et remplacée par `COleDocument` (cette nouvelle organisation facilite la création d’applications conteneur/serveur). Il existe un **#define** qui correspond à pour `COleClientDoc` `COleDocument` simplifier le portage des applications MFC/OLE1 vers MFC/OLE 2, comme OCLIENT. L’une des fonctionnalités non fournies par `COleDocument` qui étaient fournies par `COleClientDoc` est les entrées de la table des messages de commandes standard. Cela permet de faire en sorte que les applications serveur, qui utilisent également `COleDocument` (indirectement), ne les chargent pas de ces gestionnaires de commandes, sauf s’il s’agit d’une application conteneur/serveur. Vous devez ajouter les entrées suivantes à la table des messages CMainDoc :

```cpp
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE, OnUpdatePasteMenu)
ON_UPDATE_COMMAND_UI(ID_EDIT_PASTE_LINK, OnUpdatePasteLinkMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_LINKS, OnUpdateEditLinksMenu)
ON_COMMAND(ID_OLE_EDIT_LINKS, COleDocument::OnEditLinks)
ON_UPDATE_COMMAND_UI(ID_OLE_VERB_FIRST, OnUpdateObjectVerbMenu)
ON_UPDATE_COMMAND_UI(ID_OLE_EDIT_CONVERT, OnUpdateObjectVerbMenu)
ON_COMMAND(ID_OLE_EDIT_CONVERT, OnEditConvert)
```

L’implémentation de toutes ces commandes est dans `COleDocument` , qui est la classe de base de votre document.

À ce stade, OCLIENT est une application de conteneur OLE fonctionnelle. Il est possible d’insérer des éléments de n’importe quel type (OLE1 ou OLE 2). Étant donné que le code nécessaire pour activer l’activation sur place n’est pas implémenté, les éléments sont modifiés dans une fenêtre distincte comme avec OLE1. La section suivante traite des modifications nécessaires pour activer la modification sur place (parfois appelée « modification visuelle »).

### <a name="adding-visual-editing"></a>Ajout de « modifications visuelles »

L’une des fonctionnalités les plus intéressantes d’OLE est l’activation sur place (ou « modification visuelle »). Cette fonctionnalité permet à l’application serveur de prendre en charge des portions de l’interface utilisateur du conteneur pour fournir une interface de modification plus transparente pour l’utilisateur. Pour implémenter l’activation sur place dans OCLIENT, vous devez ajouter des ressources spéciales, ainsi que du code supplémentaire. Ces ressources et le code sont normalement fournis par AppWizard : en fait, une grande partie du code a été empruntée directement à partir d’une nouvelle application AppWizard avec la prise en charge de « conteneur ».

Tout d’abord, il est nécessaire d’ajouter une ressource de menu à utiliser lorsqu’un élément est actif sur place. Vous pouvez créer cette ressource de menu supplémentaire dans Visual C++ en copiant la ressource IDR_OCLITYPE et en supprimant toutes les fenêtres contextuelles sauf les fichiers et fenêtres. Deux barres de séparation sont insérées entre les fenêtres contextuelles de fichier et de fenêtre pour indiquer la séparation des groupes (elle doit ressembler à ceci : fichier &#124;&#124; fenêtre). Pour plus d’informations sur la signification de ces séparateurs et sur la façon dont les menus du serveur et du conteneur sont fusionnés, consultez [menus et ressources : fusion de menus](../mfc/menus-and-resources-menu-merging.md).

Une fois que vous avez créé ces menus, vous devez faire en sorte que l’infrastructure en ait connaissance. Pour ce faire, appelez `CDocTemplate::SetContainerInfo` pour le modèle de document avant de l’ajouter à la liste des modèles de document dans InitInstance. Le nouveau code permettant d’inscrire le modèle de document ressemble à ceci :

```cpp
CDocTemplate* pTemplate = new CMultiDocTemplate(
    IDR_OLECLITYPE,
    RUNTIME_CLASS(CMainDoc),
    RUNTIME_CLASS(CMDIChildWnd), // standard MDI child frame
    RUNTIME_CLASS(CMainView));

pTemplate->SetContainerInfo(IDR_OLECLITYPE_INPLACE);

AddDocTemplate(pTemplate);
```

La ressource IDR_OLECLITYPE_INPLACE est la ressource sur place spéciale créée dans Visual C++.

Pour activer l’activation sur place, certains éléments doivent être modifiés dans la `CView` classe dérivée (fonction CMainView), ainsi que dans la `COleClientItem` classe dérivée (CRectItem). Toutes ces substitutions sont fournies par AppWizard et la majeure partie de l’implémentation provient directement d’une application AppWizard par défaut.

Dans la première étape de ce port, l’activation sur place est entièrement désactivée en remplaçant `COleClientItem::CanActivate` . Ce remplacement doit être supprimé pour permettre l’activation sur place. En outre, la valeur NULL a été transmise à tous les appels à `DoVerb` (il en existe deux) parce que la fourniture de la vue était nécessaire uniquement pour l’activation sur place. Pour implémenter entièrement l’activation sur place, il est nécessaire de passer la vue appropriée dans l' `DoVerb` appel. L’un de ces appels est le `CMainView::OnInsertObject` suivant :

```cpp
pItem->DoVerb(OLEIVERB_SHOW, this);
```

Une autre se trouve dans `CMainView::OnLButtonDblClk` :

```cpp
m_pSelection->DoVerb(OLEIVERB_PRIMARY, this);
```

Il est nécessaire de remplacer `COleClientItem::OnGetItemPosition` . Cela indique au serveur où placer sa fenêtre par rapport à la fenêtre du conteneur lorsque l’élément est activé sur place. Pour OCLIENT, l’implémentation est simple :

```cpp
void CRectItem::OnGetItemPosition(CRect& rPosition)
{
    rPosition = m_rect;
}
```

La plupart des serveurs implémentent également ce qui est appelé « redimensionnement sur place ». Cela permet à la fenêtre du serveur d’être dimensionnée et déplacée pendant que l’utilisateur modifie l’élément. Le conteneur doit participer à cette action, car le déplacement ou le redimensionnement de la fenêtre affecte généralement la position et la taille dans le document conteneur lui-même. L’implémentation pour OCLIENT synchronise le rectangle interne géré par m_rect avec la nouvelle position et la nouvelle taille.

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

À ce stade, il existe suffisamment de code pour permettre à un élément d’être activé sur place et pour gérer le dimensionnement et le déplacement de l’élément lorsqu’il est actif, mais aucun code ne permettra à l’utilisateur de quitter la session d’édition. Bien que certains serveurs fournissent cette fonctionnalité eux-mêmes en gérant la clé d’échappement, il est préférable que les conteneurs offrent deux moyens de désactiver un élément : (1) en cliquant à l’extérieur de l’élément et (2) en appuyant sur la touche ÉCHAP.

Pour la touche ÉCHAP, ajoutez un accélérateur avec Visual C++ qui mappe la clé VK_ESCAPE à une commande, ID_CANCEL_EDIT est ajouté aux ressources. Le gestionnaire de cette commande est le suivant :

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

Pour gérer le cas où l’utilisateur clique à l’extérieur de l’élément, ajoutez le code suivant au début de `CMainView::SetSelection` :

```cpp
if (pNewSel != m_pSelection || pNewSel == NULL)
{
    COleClientItem* pActiveItem =
        GetDocument()->GetInPlaceActiveItem(this);
    if (pActiveItem != NULL&& pActiveItem != pNewSel)
        pActiveItem->Close();
}
```

Lorsqu’un élément est actif sur place, il doit avoir le focus. Pour vous assurer que c’est le cas, vous gérez OnSetFocus afin que le focus soit toujours transféré à l’élément actif lorsque votre vue reçoit le focus :

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

Lorsque la vue est redimensionnée, vous devez notifier l’élément actif que le rectangle de découpage a changé. Pour ce faire, vous devez fournir un gestionnaire pour `OnSize` :

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

## <a name="case-study-hiersvr-from-mfc-20"></a>Étude de cas : HIERSVR de MFC 2,0

[HIERSVR](../overview/visual-cpp-samples.md) était également inclus dans MFC 2,0 et implémentait OLE avec MFC/OLE1. Cette note décrit brièvement les étapes de la conversion initiale de cette application pour utiliser les classes MFC/OLE 2. Un certain nombre de fonctionnalités ont été ajoutées après la fin du port initial pour mieux illustrer les classes MFC/OLE 2. Ces fonctionnalités ne seront pas couvertes ici. Pour plus d’informations sur ces fonctionnalités avancées, reportez-vous à l’exemple lui-même.

> [!NOTE]
> Les erreurs du compilateur et le processus pas à pas ont été créés avec Visual C++ 2,0. Des messages d’erreur et des emplacements spécifiques ont peut-être été modifiés avec Visual C++ 4,0, mais les informations conceptuelles restent valides.

### <a name="getting-it-up-and-running"></a>Mise en service

L’approche adoptée pour porter l’exemple HIERSVR vers MFC/OLE consiste à commencer par la générer et à résoudre les erreurs de compilateur évidentes qui en résultent. Si vous prenez l’exemple HIERSVR dans MFC 2,0 et le compilez sous cette version de MFC, vous constaterez qu’il n’y a pas beaucoup d’erreurs à résoudre (bien qu’il y en ait plus qu’avec l’exemple OCLIENT). Les erreurs dans l’ordre dans lequel elles se produisent habituellement sont décrites ci-dessous.

### <a name="compile-and-fix-errors"></a>Compiler et corriger les erreurs

```Output
\hiersvr\hiersvr.cpp(83) : error C2039: 'RunEmbedded' : is not a member of 'COleTemplateServer'
```

Cette première erreur indique un problème bien plus important avec la `InitInstance` fonction pour les serveurs. L’initialisation requise pour un serveur OLE est probablement l’une des plus importantes modifications que vous devrez apporter à votre application MFC/OLE1 pour la faire fonctionner. La meilleure chose à faire est d’examiner ce que AppWizard crée pour un serveur OLE et de modifier votre code comme il convient. Voici quelques points à prendre en compte :

Il est nécessaire d’initialiser les bibliothèques OLE en appelant `AfxOleInit`

Appelez SetServerInfo sur l’objet de modèle de document pour définir des handles de ressource de serveur et des informations de classe d’exécution que vous ne pouvez pas définir avec le `CDocTemplate` constructeur.

N’affiche pas la fenêtre principale de votre application si/Embedding est présent sur la ligne de commande.

Vous aurez besoin d’un **GUID** pour votre document. Il s’agit d’un identificateur unique pour le type de votre document (128 bits). AppWizard en créera un pour vous. par conséquent, si vous utilisez la technique décrite ici pour copier le nouveau code à partir d’une nouvelle application serveur générée par AppWizard, vous pouvez simplement « voler » le GUID à partir de cette application. Si ce n’est pas le cas, vous pouvez utiliser l’utilitaire GUIDGEN.EXE dans le répertoire BIN.

Il est nécessaire de « connecter » votre `COleTemplateServer` objet au modèle de document en appelant `COleTemplateServer::ConnectTemplate` .

Mettez à jour le registre système lorsque votre application est exécutée de manière autonome. De cette façon, si l’utilisateur déplace le. EXE pour votre application, son exécution à partir de son nouvel emplacement met à jour la base de données d’inscription système Windows pour qu’elle pointe vers le nouvel emplacement.

Après avoir appliqué toutes ces modifications en fonction de ce que AppWizard crée pour `InitInstance` , le `InitInstance` (et le GUID associé) pour HIERSVR doivent être lus comme suit :

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

Vous remarquerez que le code ci-dessus fait référence à un nouvel ID de ressource, IDR_HIERSVRTYPE_SRVR_EMB. Il s’agit de la ressource de menu à utiliser lorsqu’un document incorporé dans un autre conteneur est modifié. Dans MFC/OLE1, les éléments de menu spécifiques à la modification d’un élément incorporé ont été modifiés à la volée. En utilisant une structure de menus totalement différente lors de la modification d’un élément incorporé au lieu de modifier un document basé sur des fichiers, il est beaucoup plus facile de fournir différentes interfaces utilisateur pour ces deux modes distincts. Comme vous le verrez plus tard, une ressource de menu entièrement distincte est utilisée lors de la modification d’un objet incorporé sur place.

Pour créer cette ressource, chargez le script de ressources dans Visual C++ et copiez la ressource de menu IDR_HIERSVRTYPE existante. Renommez la nouvelle ressource en IDR_HIERSVRTYPE_SRVR_EMB (il s’agit de la même convention d’affectation de noms que celle utilisée par AppWizard). Ensuite, remplacez « File Save » par « file Update ». Donnez-lui un ID de commande ID_FILE_UPDATE. Remplacez également « File Save As » par « File Save Copy As ». Donnez-lui un ID de commande ID_FILE_SAVE_COPY_AS. L’infrastructure fournit l’implémentation de ces deux commandes.

```Output
\hiersvr\svritem.h(60) : error C2433: 'OLESTATUS' : 'virtual' not permitted on data declarations
\hiersvr\svritem.h(60) : error C2501: 'OLESTATUS' : missing decl-specifiers
\hiersvr\svritem.h(60) : error C2146: syntax error : missing ';' before identifier 'OnSetData'
\hiersvr\svritem.h(60) : error C2061: syntax error : identifier 'OLECLIPFORMAT'
\hiersvr\svritem.h(60) : error C2501: 'OnSetData' : missing decl-specifiers
```

Il y a un certain nombre d’erreurs résultant de la substitution de `OnSetData` , car elle fait référence au type **l OleStatus** . **L OleStatus** était la manière dont OLE1 a retourné des erreurs. Cela a été remplacé par **HRESULT** dans OLE 2, bien que MFC convertisse généralement un **HRESULT** en une `COleException` contenant l’erreur. Dans ce cas particulier, la substitution de `OnSetData` n’est plus nécessaire. par conséquent, le plus simple est de le supprimer.

```Output
\hiersvr\svritem.cpp(30) : error C2660: 'COleServerItem::COleServerItem' : function does not take 1 parameters
```

Le `COleServerItem` constructeur prend un paramètre’bool’supplémentaire. Cet indicateur détermine la façon dont la gestion de la mémoire est effectuée sur les `COleServerItem` objets. En lui affectant la valeur TRUE, le Framework gère la gestion de la mémoire de ces objets, en les supprimant lorsqu’ils ne sont plus nécessaires. HIERSVR utilise `CServerItem` (dérivée de `COleServerItem` ) des objets dans le cadre de ses données natives. vous allez donc définir cet indicateur sur false. Cela permet à HIERSVR de déterminer à quel moment chaque élément de serveur est supprimé.

```Output
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
\hiersvr\svritem.cpp(44) : error C2259: 'CServerItem' : illegal attempt to instantiate abstract class
```

Comme ces erreurs l’impliquent, il existe certaines fonctions « purement virtuelles » qui n’ont pas été remplacées dans CServerItem. Cela est probablement dû au fait que la liste de paramètres de OnDraw a changé. Pour corriger cette erreur, modifiez `CServerItem::OnDraw` comme suit (ainsi que la déclaration dans svritem. h) :

```cpp
BOOL CServerItem::OnDraw(CDC* pDC, CSize& rSize)
{
    // request from OLE to draw node
    pDC->SetMapMode(MM_TEXT); // always in pixels
    return DoDraw(pDC, CPoint(0, 0), FALSE);
}
```

Le nouveau paramètre est « rSize ». Cela vous permet de remplir la taille du dessin, si vous le souhaitez. Cette taille doit être dans **HIMETRIC**. Dans ce cas, il n’est pas pratique de remplir cette valeur dans, de sorte que l’infrastructure appelle `OnGetExtent` pour récupérer l’étendue. Pour que cela fonctionne, vous devez implémenter `OnGetExtent` :

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

Dans la fonction CServerItem :: CalcNodeSize, la taille de l’élément est convertie en **HIMETRIC** et stockée dans *m_rectBounds*. Le membre'*m_rectBounds*'non documenté de `COleServerItem` n’existe pas (il a été partiellement remplacé par *M_SIZEEXTENT*, mais dans OLE 2, ce membre a une utilisation légèrement différente de *m_rectBounds* dans OLE1). Au lieu de définir la taille de **HIMETRIC** dans cette variable membre, vous allez la retourner. Cette valeur de retour est utilisée dans `OnGetExtent` , implémenté précédemment.

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

CServerItem remplace également `COleServerItem::OnGetTextData` . Cette fonction est obsolète dans MFC/OLE et est remplacée par un autre mécanisme. La version MFC 3,0 de l’exemple MFC OLE [HIERSVR](../overview/visual-cpp-samples.md) implémente cette fonctionnalité en remplaçant `COleServerItem::OnRenderFileData` . Cette fonctionnalité n’étant pas importante pour ce port de base, vous pouvez supprimer le remplacement OnGetTextData.

Il y a beaucoup d’autres erreurs dans svritem. cpp qui n’ont pas été traitées. Ce ne sont pas des erreurs « réelles », mais simplement des erreurs provoquées par des erreurs précédentes.

```Output
\hiersvr\svrview.cpp(325) : error C2660: 'CopyToClipboard' : function does not take 2 parameters
```

`COleServerItem::CopyToClipboard` ne prend plus en charge l' `bIncludeNative` indicateur. Les données natives (les données écrites par la fonction Serialize de l’élément de serveur) sont toujours copiées. vous supprimez donc le premier paramètre. De plus, `CopyToClipboard` lèvera une exception lorsqu’une erreur se produit au lieu de retourner false. Modifiez le code de CServerView :: OnEditCopy comme suit :

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

Bien qu’il y ait plus d’erreurs résultant de la compilation de la version MFC 2,0 de HIERSVR que pour la même version d’OCLIENT, il y avait en fait moins de modifications.

À ce stade, HIERSVR se compile et lie et fonctionne en tant que serveur OLE, mais sans la fonctionnalité de modification sur place, qui sera implémentée ensuite.

### <a name="adding-visual-editing"></a>Ajout de « modifications visuelles »

Pour ajouter la « modification visuelle » (ou l’activation sur place) à cette application serveur, il ne vous reste plus que quelques points à prendre en charge :

- Vous avez besoin d’une ressource de menu spéciale à utiliser lorsque l’élément est actif sur place.

- Cette application comporte une barre d’outils. vous avez donc besoin d’une barre d’outils avec seulement un sous-ensemble de la barre d’outils normale pour correspondre aux commandes de menu disponibles sur le serveur (correspond à la ressource de menu mentionnée ci-dessus).

- Vous avez besoin d’une nouvelle classe dérivée de `COleIPFrameWnd` qui fournit l’interface utilisateur sur place (à l’instar de CMainFrame, dérivée de `CMDIFrameWnd` , qui fournit l’interface utilisateur MDI).

- Vous devez indiquer à l’infrastructure les ressources et classes spéciales.

La ressource de menu est facile à créer. Exécutez Visual C++, copiez la ressource de menu IDR_HIERSVRTYPE dans une ressource de menu appelée IDR_HIERSVRTYPE_SRVR_IP. Modifiez le menu de façon à ce que seules les fenêtres de modification et de menu aide soient conservées. Ajoutez deux séparateurs au menu entre les menus d’aide et de modification (il doit ressembler à ceci : modifier &#124;&#124; aide). Pour plus d’informations sur la signification de ces séparateurs et sur la façon dont les menus du serveur et du conteneur sont fusionnés, consultez [menus et ressources : fusion de menus](../mfc/menus-and-resources-menu-merging.md).

L’image bitmap de la barre d’outils du sous-ensemble peut être facilement créée en copiant celle-ci à partir d’une nouvelle application générée par AppWizard avec l’option « serveur » activée. Cette image bitmap peut ensuite être importée dans Visual C++. Veillez à attribuer à la bitmap un ID de IDR_HIERSVRTYPE_SRVR_IP.

La classe dérivée de `COleIPFrameWnd` peut également être copiée à partir d’une application générée par AppWizard avec prise en charge du serveur. Copiez les deux fichiers, IPFRAME. CPP et IPFRAME. H et les ajouter au projet. Assurez-vous que l' `LoadBitmap` appel fait référence à IDR_HIERSVRTYPE_SRVR_IP, l’image bitmap créée à l’étape précédente.

Maintenant que toutes les nouvelles ressources et toutes les nouvelles classes sont créées, ajoutez le code nécessaire pour que l’infrastructure en sache (et sache que cette application prend désormais en charge la modification sur place). Pour ce faire, vous pouvez ajouter des paramètres supplémentaires à l' `SetServerInfo` appel de la `InitInstance` fonction :

```cpp
pDocTemplate->SetServerInfo(IDR_HIERSVRTYPE_SRVR_EMB,
    IDR_HIERSVRTYPE_SRVR_IP,
    RUNTIME_CLASS(CInPlaceFrame));
```

Elle est maintenant prête à être exécutée sur place dans n’importe quel conteneur qui prend également en charge l’activation sur place. Toutefois, il existe un bogue mineur qui se cache dans le code. HIERSVR prend en charge un menu contextuel qui s’affiche quand l’utilisateur appuie sur le bouton droit de la souris. Ce menu fonctionne lorsque HIERSVR est entièrement ouvert, mais ne fonctionne pas lors de la modification d’une incorporation sur place. La raison peut être épinglée à cette seule ligne de code dans CServerView :: OnRButtonDown :

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetApp()->m_pMainWnd);
```

Notez la référence à `AfxGetApp()->m_pMainWnd` . Quand le serveur est activé sur place, il possède une fenêtre principale et m_pMainWnd est défini, mais il est généralement invisible. En outre, cette fenêtre fait référence à la fenêtre *principale* de l’application, la fenêtre frame MDI qui s’affiche lorsque le serveur est entièrement ouvert ou exécuté de manière autonome. Elle ne fait pas référence à la fenêtre frame active, qui lorsque l’activation sur place est une fenêtre frame dérivée de `COleIPFrameWnd` . Pour obtenir la fenêtre active correcte même en cas de modification sur place, cette version de MFC ajoute une nouvelle fonction, `AfxGetMainWnd` . En général, vous devez utiliser cette fonction au lieu de `AfxGetApp()->m_pMainWnd` . Ce code doit changer comme suit :

```cpp
pMenu->TrackPopupMenu(TPM_CENTERALIGN | TPM_RIGHTBUTTON,
    point.x,
    point.y,
    AfxGetMainWnd());
```

Vous disposez à présent d’un serveur OLE activé au minimum pour l’activation sur place fonctionnelle. Mais il existe toujours de nombreuses fonctionnalités disponibles avec MFC/OLE 2 qui n’étaient pas disponibles dans MFC/OLE1. Pour plus d’informations sur les fonctionnalités que vous pouvez souhaiter implémenter, consultez l’exemple HIERSVR. Voici quelques-unes des fonctionnalités implémentées par HIERSVR :

- Zoom, pour un vrai comportement WYSIWYG en ce qui concerne le conteneur.

- Glisser-déplacer et un format de presse-papiers personnalisé.

- Faire défiler la fenêtre de conteneur lorsque la sélection est modifiée.

L’exemple HIERSVR dans MFC 3,0 utilise également une conception légèrement différente pour ses éléments de serveur. Cela permet d’économiser de la mémoire et de rendre vos liens plus flexibles. Avec la version 2,0 de HIERSVR, chaque nœud de l’arborescence *est-a* `COleServerItem` . `COleServerItem` a un peu plus de surcharge que ce qui est strictement nécessaire pour chacun de ces nœuds, mais un `COleServerItem` est requis pour chaque lien actif. Mais dans la plupart des cas, il y a très peu de liens actifs à un moment donné. Pour rendre cette solution plus efficace, HIERSVR dans cette version de MFC sépare le nœud de `COleServerItem` . Il a à la fois un CServerNode et une `CServerItem` classe. Le `CServerItem` (dérivé de `COleServerItem` ) n’est créé que si nécessaire. Une fois que le conteneur (ou les conteneurs) s’est arrêté à l’aide de ce lien particulier vers ce nœud particulier, l’objet CServerItem associé au CServerNode est supprimé. Cette conception est plus efficace et plus flexible. Sa flexibilité est liée à la gestion de plusieurs liens de sélection. Aucune de ces deux versions de HIERSVR ne prend en charge la sélection multiple, mais il serait beaucoup plus facile d’ajouter (et de prendre en charge des liens vers ces sélections) avec la version MFC 3,0 de HIERSVR, puisque le `COleServerItem` est séparé des données natives.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

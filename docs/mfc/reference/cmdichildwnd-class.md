---
title: CMDIChildWnd, classe
ms.date: 11/04/2016
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
ms.openlocfilehash: 0fbcb47f3148b72a3155e7c17cc913d652c70c2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370082"
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd, classe

Fournit les fonctionnalités d'une fenêtre enfant d'interface multidocument (MDI) Windows, ainsi que des membres permettant de gérer la fenêtre.

## <a name="syntax"></a>Syntaxe

```
class CMDIChildWnd : public CFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construit un objet `CMDIChildWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMDIChildWnd::Créer](#create)|Crée la fenêtre pour enfant `CMDIChildWnd` Windows MDI associée à l’objet.|
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Retourne le cadre MDI parent de la fenêtre du client MDI.|
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Active cette fenêtre d’enfant MDI.|
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Détruit cette fenêtre d’enfant MDI.|
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximise cette fenêtre d’enfant MDI.|
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaure cette fenêtre d’enfant MDI de la taille maximisée ou minimisée.|
|[CMDIChildWnd::SetHandles](#sethandles)|Définit les poignées pour les ressources de menu et d’accélérateur.|

## <a name="remarks"></a>Notes

Une fenêtre d’enfant MDI ressemble beaucoup à une fenêtre de cadre typique, sauf que la fenêtre de l’enfant MDI apparaît à l’intérieur d’une fenêtre de cadre MDI plutôt que sur le bureau. Une fenêtre pour enfants MDI n’a pas de barre de menu propre, mais partage plutôt le menu de la fenêtre cadre MDI. Le cadre modifie automatiquement le menu de l’image MDI pour représenter la fenêtre d’enfant MDI actuellement active.

Pour créer une fenêtre d’enfant MDI utile `CMDIChildWnd`pour votre application, tirer une classe de . Ajoutez des variables aux membres à la classe dérivée pour stocker des données spécifiques à votre application. Implémentez des fonctions membres de gestionnaire de messages et une table des messages dans la classe dérivée pour préciser ce qu'il advient quand des messages sont dirigés vers la fenêtre.

Il y a trois façons de construire une fenêtre pour enfants MDI :

- Construisez-le `Create`directement en utilisant .

- Construisez-le `LoadFrame`directement en utilisant .

- Construisez-le indirectement à l’aide d’un modèle de document.

Avant d’appeler `Create` ou `LoadFrame`, vous devez construire l’objet de la fenêtre de cadre sur le tas à l’aide du **nouvel** opérateur C. Avant `Create` d’appeler, vous pouvez également enregistrer un cours de fenêtre avec la fonction globale [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) pour définir les styles d’icône et de classe pour le cadre.

Utilisez `Create` la fonction du membre pour passer les paramètres de création du cadre comme arguments immédiats.

`LoadFrame`nécessite moins `Create`d’arguments que , et récupère plutôt la plupart de ses valeurs par défaut à partir de ressources, y compris la légende du cadre, icône, table d’accélérateur, et le menu. Pour être `LoadFrame`accessible par , toutes ces ressources doivent avoir la même pièce d’identité de ressource (par exemple, IDR_MAINFRAME).

Lorsqu’un `CMDIChildWnd` objet contient des vues et des documents, ils sont créés indirectement par le cadre au lieu directement par le programmeur. L’objet `CDocTemplate` orchestre la création du cadre, la création des vues contenantes et la connexion des vues au document approprié. Les paramètres du `CDocTemplate` constructeur spécifient les `CRuntimeClass` trois classes concernées (document, cadre et vue). Un `CRuntimeClass` objet est utilisé par le cadre pour créer dynamiquement de nouvelles images lorsqu’il est spécifié par l’utilisateur (par exemple, en utilisant la commande Fichier Nouveau ou la nouvelle commande de fenêtre MDI).

Une classe de fenêtre `CMDIChildWnd` de cadre dérivée doit être déclarée avec DECLARE_DYNCREATE afin que le mécanisme de RUNTIME_CLASS ci-dessus fonctionne correctement.

La `CMDIChildWnd` classe hérite d’une `CFrameWnd`grande partie de sa mise en œuvre par défaut de . Pour une liste détaillée de ces fonctionnalités, veuillez consulter la description de classe [CFrameWnd.](../../mfc/reference/cframewnd-class.md) La `CMDIChildWnd` classe a les caractéristiques supplémentaires suivantes:

- En conjonction `CMultiDocTemplate` avec la `CMDIChildWnd` classe, plusieurs objets du même modèle de document partagent le même menu, économisant les ressources du système Windows.

- Le menu actuel de la fenêtre pour enfants MDI remplace entièrement le menu de la fenêtre de cadre MDI, et la légende de la fenêtre d’enfant MDI actuellement active est ajoutée à la légende de la fenêtre de cadre MDI. Pour d’autres exemples de fonctions de fenêtre pour enfants MDI `CMDIFrameWnd` qui sont mises en œuvre en conjonction avec une fenêtre de cadre MDI, voir la description de classe.

N’utilisez pas l’opérateur de **suppression** de C POUR détruire une fenêtre de cadre. Utilisez `CWnd::DestroyWindow` à la place. La `CFrameWnd` mise `PostNcDestroy` en œuvre de supprimera l’objet CMD lorsque la fenêtre sera détruite. Lorsque l’utilisateur ferme la fenêtre `OnClose` du `DestroyWindow`cadre, le gestionnaire par défaut appelle .

Pour plus `CMDIChildWnd`d’informations sur , voir [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMDIChildWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd

Appelez pour `CMDIChildWnd` construire un objet.

```
CMDIChildWnd();
```

### <a name="remarks"></a>Notes

Appelez `Create` pour créer la fenêtre visible.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMDIChildWnd::Créer](#create).

## <a name="cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Créer

Appelez cette fonction de membre pour créer une fenêtre `CMDIChildWnd` d’enfant Windows MDI et l’attacher à l’objet.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,
    const RECT& rect = rectDefault,
    CMDIFrameWnd* pParentWnd = NULL,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszClassName (en)*<br/>
Indique une chaîne de caractères à durée nulle qui nomme la classe Windows (une structure [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) Le nom de la classe peut être n’importe quel nom enregistré auprès de la fonction globale [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Devrait être NULL `CMDIChildWnd`pour une norme .

*lpszWindowName (en)*<br/>
Indique une chaîne de caractères non terminée qui représente le nom de fenêtre. Utilisé comme texte pour la barre de titre.

*dwStyle (en)*<br/>
Spécifie les attributs de [style](../../mfc/reference/styles-used-by-mfc.md#window-styles) de fenêtre. Le style WS_CHILD est nécessaire.

*Rect*<br/>
Contient la taille et la position de la fenêtre. La `rectDefault` valeur permet à Windows de spécifier la taille et la position de la nouvelle `CMDIChildWnd`.

*pParentWnd*<br/>
Spécifie le parent de la fenêtre. Si NULL, la fenêtre d’application principale est utilisée.

*pContext*<br/>
Spécifie une structure [CCreateContext.](../../mfc/reference/ccreatecontext-structure.md) Ce paramètre peut être NULL.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

La fenêtre d’image d’enfant MDI actuellement active peut déterminer la légende de la fenêtre de cadre parent. Cette fonctionnalité est désactivée en éteignant le FWS_ADDTOTITLE morceau de style de la fenêtre de cadre enfant.

Le cadre appelle cette fonction de membre en réponse à une commande d’utilisateur pour créer une fenêtre d’enfant, et le cadre utilise le *paramètre pContext* pour connecter correctement la fenêtre de l’enfant à l’application. Lorsque vous `Create`appelez, *pContext* peut être NULL.

### <a name="example"></a>Exemple

Exemple 1 :

[!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]

### <a name="example"></a>Exemple

Exemple 2 :

[!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]

[!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]

## <a name="cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame

Appelez cette fonction pour retourner le cadre parent MDI.

```
CMDIFrameWnd* GetMDIFrame();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre de cadre parent MDI.

### <a name="remarks"></a>Notes

Le cadre retourné est deux `CMDIChildWnd` parents retirés de la et est le parent `CMDIChildWnd` de la fenêtre de type MDICLIENT qui gère l’objet. Appelez la fonction membre [GetParent](../../mfc/reference/cwnd-class.md#getparent) pour renvoyer le parent MDICLIENT immédiat de l’objet `CMDIChildWnd` comme pointeur temporaire. `CWnd`

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).

## <a name="cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIActivate

Appelez cette fonction de membre pour activer une fenêtre d’enfant MDI indépendamment de la fenêtre de cadre MDI.

```
void MDIActivate();
```

### <a name="remarks"></a>Notes

Lorsque le cadre devient actif, la fenêtre de l’enfant qui a été activée pour la dernière fois sera également activée.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).

## <a name="cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy

Appelez cette fonction de membre pour détruire une fenêtre d’enfant MDI.

```
void MDIDestroy();
```

### <a name="remarks"></a>Notes

La fonction membre enlève le titre de la fenêtre de l’enfant de la fenêtre du cadre et désactive la fenêtre de l’enfant.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]

## <a name="cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize

Appelez cette fonction de membre pour maximiser une fenêtre d’enfant MDI.

```
void MDIMaximize();
```

### <a name="remarks"></a>Notes

Lorsqu’une fenêtre pour enfants est maximisée, Windows la resize pour que sa zone client remplisse la zone cliente de la fenêtre du cadre. Windows place le menu de contrôle de la fenêtre de l’enfant dans la barre de menu du cadre afin que l’utilisateur puisse restaurer ou fermer la fenêtre de l’enfant et ajoute le titre de la fenêtre de l’enfant au titre de la fenêtre de cadre.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]

## <a name="cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore

Appelez cette fonction de membre pour restaurer une fenêtre d’enfant MDI de taille maximisée ou minimisée.

```
void MDIRestore();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]

## <a name="cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles

Définit les poignées pour les ressources de menu et d’accélérateur.

```
void SetHandles(
    HMENU hMenu,
    HACCEL hAccel);
```

### <a name="parameters"></a>Paramètres

*hMenu*<br/>
Le manche d’une ressource de menu.

*hAccel (en)*<br/>
Le manche d’une ressource d’accélérateur.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir le menu et les ressources d’accélérateur utilisées par l’objet de fenêtre pour enfant MDI.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC Échantillon MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CMDIFrameWnd, classe](../../mfc/reference/cmdiframewnd-class.md)

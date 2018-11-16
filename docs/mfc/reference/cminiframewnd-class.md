---
title: CMiniFrameWnd, classe
ms.date: 11/04/2016
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
ms.openlocfilehash: a6fdef34ba5873718caed509100cbe7e905d880d
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693521"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd, classe

Représente une fenêtre frame de demi-hauteur généralement visible autour de barres d'outils flottantes.

## <a name="syntax"></a>Syntaxe

```
class CMiniFrameWnd : public CFrameWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Construit un objet `CMiniFrameWnd`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMiniFrameWnd::Create](#create)|Crée un `CMiniFrameWnd` objet après la construction.|
|[CMiniFrameWnd::CreateEx](#createex)|Crée un `CMiniFrameWnd` objet (avec des options supplémentaires) après la construction.|

## <a name="remarks"></a>Notes

Ces fenêtres mini-frame se comportent comme les fenêtres de frame normal, sauf qu’ils n’ont pas de boutons Réduire/agrandir ou de menus et vous suffit de cliquer sur le menu système pour faire disparaître les.

Pour utiliser un `CMiniFrameWnd` de l’objet, commencez par définir l’objet. Appelez ensuite la [créer](#create) fonction membre pour afficher la fenêtre mini-frame.

Pour plus d’informations sur l’utilisation `CMiniFrameWnd` objets, consultez l’article [ancrées et flottantes les barres d’outils](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd

Construit un `CMiniFrameWnd` de l’objet, mais ne crée pas de la fenêtre.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Notes

Pour créer la fenêtre, appelez [CMiniFrameWnd::Create](#create).

##  <a name="create"></a>  CMiniFrameWnd::Create

Crée la fenêtre mini-frame Windows et l’attache à la `CMiniFrameWnd` objet.

```
virtual BOOL Create(
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Paramètres

*lpClassName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui nomme la classe Windows. Le nom de classe peut être n’importe quel nom inscrit avec global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) (fonction). Si NULL, la classe de fenêtre est inscrit pour vous par l’infrastructure. MFC fournit la classe par défaut, les styles et les attributs suivants :

- CS_DBLCLKS, qui envoie des messages à la procédure de fenêtre de double lorsque l’utilisateur double-clique sur la souris de bit de style de jeux.

- Définit les bits de style CS_HREDRAW et CS_VREDRAW, qui demandent le contenu de la zone cliente à être redessiné lors de la taille de la fenêtre change.

- Définit le curseur de la classe à la IDC_ARROW standard de Windows.

- Définit le pinceau d’arrière-plan de classe avec la valeur NULL, afin de la fenêtre n’efface pas son arrière-plan.

- Définit l’icône de classe sur l’icône du logo Windows standard, drapeau.

- Définit la fenêtre à la taille par défaut et la position, comme indiqué par Windows.

*lpWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui contient le nom de la fenêtre.

*dwStyle*<br/>
Spécifie les attributs de style de fenêtre. Celles-ci peuvent inclure des styles de fenêtre standard et un ou plusieurs des styles spéciaux suivants :

- MFS_MOVEFRAME permet la fenêtre mini-frame à déplacer en cliquant sur n’importe quel bord de la fenêtre, pas seulement la légende.

- MFS_4THICKFRAME désactive le redimensionnement de la fenêtre mini-frame.

- MFS_SYNCACTIVE synchronise l’activation de la fenêtre mini-frame à l’activation de sa fenêtre parente.

- La fenêtre mini-frame être dimensionnés aussi petit que le contenu de la zone cliente MFS_THICKFRAME permet d’autoriser.

- MFS_BLOCKSYSMENU désactive l’accès au menu système et le menu de contrôle et les convertit en partie de la légende (barre de titre).

Consultez [CWnd::Create](../../mfc/reference/cwnd-class.md#create) pour obtenir une description des valeurs de style de fenêtre possible. La combinaison classique utilisée pour les fenêtres mini-frame est WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.

*Rect*<br/>
Un `RECT` structure qui spécifie les dimensions souhaitées de la fenêtre.

*pParentWnd*<br/>
Pointe vers la fenêtre parente. Utilisez NULL pour les fenêtres de niveau supérieur.

*nID*<br/>
Si la fenêtre mini-frame est créée comme une fenêtre enfant, il s’agit de l’identificateur du contrôle enfant ; sinon 0.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Create` Initialise le nom de la classe de la fenêtre et le nom de la fenêtre et enregistre les valeurs par défaut pour son style et le parent.

##  <a name="createex"></a>  CMiniFrameWnd::CreateEx

Crée un objet `CMiniFrameWnd`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    LPCTSTR lpClassName,
    LPCTSTR lpWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd = NULL,
    UINT nID = 0);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu de la `CMiniFrameWnd` en cours de création. Appliquer une partie de la [les styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) à la fenêtre.

*lpClassName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui nomme la classe Windows (un [WNDCLASS](/windows/desktop/api/winuser/ns-winuser-tagwndclassa) structure). Le nom de classe peut être n’importe quel nom inscrit avec global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) fonction ou l’un des noms de classe de contrôle prédéfini. Il ne doit pas être NULL.

*lpWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par null qui contient le nom de la fenêtre.

*dwStyle*<br/>
Spécifie les attributs de style de fenêtre. Consultez [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [CWnd::Create](../../mfc/reference/cwnd-class.md#create) pour obtenir une description des valeurs possibles.

*Rect*<br/>
La taille et la position de la fenêtre, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parent.

*nID*<br/>
L’identificateur de la fenêtre enfant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Le `CreateEx` paramètres spécifient le WNDCLASS, le style de fenêtre et la position initiale (éventuellement) et la taille de la fenêtre. `CreateEx` Spécifie également la fenêtre parent (le cas échéant) et code.

Lorsque `CreateEx` s’exécute, les envois de Windows le [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) messages dans la fenêtre.

Pour étendre la gestion de message par défaut, dérivez une classe de `CMiniFrameWnd`, ajouter une table des messages à la nouvelle classe et de fournir des fonctions membres pour les messages ci-dessus. Substituer `OnCreate`, par exemple, pour effectuer une initialisation nécessaire pour une nouvelle classe.

Substituer davantage `On` *Message* gestionnaires pour ajouter d’autres fonctionnalités à votre classe dérivée de messages.

Si le style WS_VISIBLE est indiqué, Windows envoie tous les messages qui sont requises pour activer et afficher la fenêtre à la fenêtre. Si le style de fenêtre spécifie une barre de titre, le titre de la fenêtre vers laquelle pointe le *lpszWindowName* paramètre s’affiche dans la barre de titre.

Le *dwStyle* paramètre peut être n’importe quelle combinaison de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Les fenêtres de boîte à outils de Palette style ancien ne sont plus prises en charge. L’ancien style, ce qui n’avait pas d’un bouton de fermeture « X », a été pris en charge lors de l’exécution d’une application MFC dans les versions précédentes de Windows, mais n’est plus pris en charge dans Visual C++ .NET. Le nouveau style WS_EX_TOOLWINDOW est maintenant pris en charge ; Pour obtenir une description de ce style, consultez [Styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Voir aussi

[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)

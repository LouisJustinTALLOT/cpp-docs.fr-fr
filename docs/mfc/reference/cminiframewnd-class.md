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
ms.openlocfilehash: e9b91161f4207f4d2215d8777beade93617ddfac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319821"
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
|[CMiniFrameWnd::Créer](#create)|Crée `CMiniFrameWnd` un objet après la construction.|
|[CMiniFrameWnd::CreateEx](#createex)|Crée `CMiniFrameWnd` un objet (avec des options supplémentaires) après la construction.|

## <a name="remarks"></a>Notes

Ces fenêtres à mini-cadre se comportent comme des fenêtres à ossature normale, sauf qu’elles n’ont pas de boutons ou de menus de minimisation/maximisation et qu’il suffit de cliquer sur le menu du système pour les rejeter.

Pour utiliser `CMiniFrameWnd` un objet, définissez d’abord l’objet. Ensuite, appelez la fonction membre [Create](#create) pour afficher la fenêtre mini-cadre.

Pour plus d’informations `CMiniFrameWnd` sur la façon d’utiliser des objets, voir l’article [Docking and Floating Toolbars](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd

Construit un `CMiniFrameWnd` objet, mais ne crée pas la fenêtre.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Notes

Pour créer la fenêtre, appelez [CMiniFrameWnd::Créer](#create).

## <a name="cminiframewndcreate"></a><a name="create"></a>CMiniFrameWnd::Créer

Crée la fenêtre Windows mini-cadre et `CMiniFrameWnd` la fixe à l’objet.

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

*lpClassName (en)*<br/>
Indique une chaîne de caractères à durée nulle qui nomme la classe Windows. Le nom de la classe peut être n’importe quel nom enregistré auprès de la fonction mondiale [AfxRegisterWndClass.](application-information-and-management.md#afxregisterwndclass) Si NULL, le cours de fenêtre sera enregistré pour vous par le cadre. MFC donne à la classe par défaut les styles et les attributs suivants :

- Définit le bit de style CS_DBLCLKS, qui envoie des messages en double clic à la procédure de fenêtre lorsque l’utilisateur double-clics de la souris.

- Définit les bits de style CS_HREDRAW et CS_VREDRAW, qui dirigent le contenu de la zone client à redessiner lorsque la fenêtre change de taille.

- Définit le curseur de classe à la norme Windows IDC_ARROW.

- Définit la brosse de fond de classe à NULL, de sorte que la fenêtre n’effacera pas son arrière-plan.

- Définit l’icône de classe à la norme, en agitant l’icône du logo Windows.

- Définit la fenêtre à la taille et la position par défaut, comme indiqué par Windows.

*lpWindowName*<br/>
Indique une chaîne de caractères non terminée qui contient le nom de fenêtre.

*dwStyle (en)*<br/>
Spécifie les attributs de style de fenêtre. Ceux-ci peuvent inclure des styles de fenêtre standard et un ou plusieurs des styles spéciaux suivants:

- MFS_MOVEFRAME permet de déplacer la mini-fenêtre de cadre en cliquant sur n’importe quel bord de la fenêtre, et pas seulement la légende.

- MFS_4THICKFRAME Désactive la rédimensionnement de la fenêtre mini-cadre.

- MFS_SYNCACTIVE synchronise l’activation de la mini-fenêtre de cadre à l’activation de sa fenêtre parente.

- MFS_THICKFRAME permet de tailler la mini-fenêtre à ossature aussi petite que le contenu de la zone cliente.

- MFS_BLOCKSYSMENU désactive l’accès au menu du système et au menu de contrôle, et les convertit en une partie de la légende (barre de titre).

Voir [CWnd::Créer](../../mfc/reference/cwnd-class.md#create) pour une description des valeurs possibles de style de fenêtre. La combinaison typique utilisée pour les fenêtres à mini-cadre est WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.

*Rect*<br/>
Une `RECT` structure spécifiant les dimensions souhaitées de la fenêtre.

*pParentWnd*<br/>
Points à la fenêtre parent. Utilisez NULL pour les fenêtres de haut niveau.

*nID*<br/>
Si la fenêtre mini-cadre est créée comme une fenêtre enfant, c’est l’identifiant du contrôle de l’enfant; sinon 0.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Create`initialise le nom de classe et le nom de fenêtre de la fenêtre de la fenêtre et enregistre les valeurs par défaut pour son style et son parent.

## <a name="cminiframewndcreateex"></a><a name="createex"></a>CMiniFrameWnd::CreateEx

Crée un objet `CMiniFrameWnd` .

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

*dwExStyle (en anglais)*<br/>
Spécifie le `CMiniFrameWnd` style étendu de la création. Appliquez n’importe lequel des [styles de fenêtre étendu](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) à la fenêtre.

*lpClassName (en)*<br/>
Indique une chaîne de caractères à durée nulle qui nomme la classe Windows (une structure [WNDCLASS).](/windows/win32/api/winuser/ns-winuser-wndclassw) Le nom de classe peut être n’importe quel nom enregistré auprès de la fonction [mondiale AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) ou de l’un des noms prédéfinis de classe de contrôle. Ce ne doit pas être NULL.

*lpWindowName*<br/>
Indique une chaîne de caractères non terminée qui contient le nom de fenêtre.

*dwStyle (en)*<br/>
Spécifie les attributs de style de fenêtre. Voir [Windows Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [CWnd::Créer](../../mfc/reference/cwnd-class.md#create) pour une description des valeurs possibles.

*Rect*<br/>
La taille et la position de la fenêtre, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Points à l’objet de fenêtre parent.

*nID*<br/>
L’identifiant de la fenêtre de l’enfant.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Les `CreateEx` paramètres spécifient le WNDCLASS, le style de fenêtre, et (optionnellement) la position initiale et la taille de la fenêtre. `CreateEx`spécifie également le parent de la fenêtre (le cas échéant) et l’identification.

Lors `CreateEx` de l’exécution, Windows envoie le [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), et [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) messages à la fenêtre.

Pour étendre la manipulation par défaut `CMiniFrameWnd`des messages, extraire une classe, ajouter une carte de message à la nouvelle classe et fournir des fonctions aux membres pour les messages ci-dessus. `OnCreate`Remplacer, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Remplacez `On`d’autres gestionnaires de messages *message* pour ajouter d’autres fonctionnalités à votre classe dérivée.

Si le style WS_VISIBLE est donné, Windows envoie à la fenêtre tous les messages nécessaires pour activer et afficher la fenêtre. Si le style de fenêtre spécifie une barre de titre, le titre de fenêtre indiqué par le paramètre *lpszWindowName* est affiché dans la barre de titre.

Le paramètre *dwStyle* peut être n’importe quelle combinaison de styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Les fenêtres de boîte à outils Palette de style ancien ne sont plus prises en charge. L’ancien style, qui n’avait pas de bouton "X" Close, a été pris en charge lors de l’exécution d’une application MFC sur les versions précédentes de Windows, mais n’est plus pris en charge dans Visual C.NET. Seul le nouveau style WS_EX_TOOLWINDOW est maintenant pris en charge; pour une description de ce style, voir [Extended Window Styles](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Voir aussi

[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)

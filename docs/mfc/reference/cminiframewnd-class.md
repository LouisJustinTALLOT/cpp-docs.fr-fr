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
ms.openlocfilehash: 45b4698cc70487a6c3fe1470fe27f7b5c4f95402
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504603"
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

Ces fenêtres mini-frame se comportent comme des fenêtres Frame normales, sauf qu’elles n’ont pas de boutons ou de menus réduire/agrandir et que vous n’avez qu’à cliquer une seule fois sur le menu système pour les faire disparaître.

Pour utiliser un `CMiniFrameWnd` objet, commencez par définir l’objet. Appelez ensuite la fonction membre [Create](#create) pour afficher la fenêtre mini-frame.

Pour plus d’informations sur l’utilisation `CMiniFrameWnd` des objets, consultez l’article sur les [barres d’outils ancrées et flottantes](../../mfc/docking-and-floating-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

`CMiniFrameWnd`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd

Construit un `CMiniFrameWnd` objet, mais ne crée pas la fenêtre.

```
CMiniFrameWnd();
```

### <a name="remarks"></a>Notes

Pour créer la fenêtre, appelez [CMiniFrameWnd :: Create](#create).

##  <a name="create"></a>  CMiniFrameWnd::Create

Crée la fenêtre mini-frame Windows et l’attache à l' `CMiniFrameWnd` objet.

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
Pointe vers une chaîne de caractères se terminant par un caractère null qui nomme la classe Windows. Le nom de la classe peut être n’importe quel nom enregistré avec la fonction [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) globale. Si la valeur est NULL, la classe de fenêtre sera inscrite pour vous par le Framework. MFC donne à la classe par défaut les styles et attributs suivants :

- Définit le bit de style CS_DBLCLKS, qui envoie des messages de double-clic à la procédure de fenêtre lorsque l’utilisateur double-clique sur la souris.

- Définit les bits de style CS_HREDRAW et CS_VREDRAW, qui dirigent le contenu de la zone cliente à redessiner lorsque la fenêtre change de taille.

- Définit le curseur de la classe sur le IDC_ARROW standard Windows.

- Affecte la valeur NULL au pinceau d’arrière-plan de la classe, de sorte que la fenêtre n’efface pas son arrière-plan.

- Définit l’icône de classe sur l’icône de logo Windows standard, avec indicateur d’ondulation.

- Définit la taille et la position par défaut de la fenêtre, comme indiqué par Windows.

*lpWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui contient le nom de la fenêtre.

*dwStyle*<br/>
Spécifie les attributs de style de fenêtre. Celles-ci peuvent inclure des styles de fenêtre standard et un ou plusieurs des styles spéciaux suivants :

- MFS_MOVEFRAME permet de déplacer la fenêtre mini-frame en cliquant sur n’importe quel bord de la fenêtre, et pas seulement sur la légende.

- MFS_4THICKFRAME désactive le redimensionnement de la fenêtre mini-frame.

- MFS_SYNCACTIVE synchronise l’activation de la fenêtre mini-frame avec l’activation de sa fenêtre parente.

- MFS_THICKFRAME permet de dimensionner la fenêtre mini-frame aussi petit que le contenu de la zone client Allow.

- MFS_BLOCKSYSMENU désactive l’accès au menu système et au menu de contrôle, et les convertit en une partie de la légende (barre de titre).

Consultez [CWnd :: Create](../../mfc/reference/cwnd-class.md#create) pour obtenir une description des valeurs de style de fenêtre possibles. La combinaison classique utilisée pour les fenêtres mini-frame est&#124;WS_POPUP&#124;WS_CAPTION WS_SYSMENU.

*rect*<br/>
`RECT` Structure spécifiant les dimensions souhaitées de la fenêtre.

*pParentWnd*<br/>
Pointe vers la fenêtre parente. Utilisez la valeur NULL pour les fenêtres de niveau supérieur.

*nID*<br/>
Si la fenêtre mini-frame est créée en tant que fenêtre enfant, il s’agit de l’identificateur du contrôle enfant ; Sinon, 0.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Create`Initialise le nom de la classe et le nom de la fenêtre de la fenêtre et enregistre les valeurs par défaut de son style et de son parent.

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
Spécifie le style étendu du `CMiniFrameWnd` en cours de création. Appliquez l’un des [styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) à la fenêtre.

*lpClassName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui nomme la classe Windows (structure [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) ). Le nom de la classe peut être n’importe quel nom enregistré avec la fonction [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) globale ou l’un des noms de classe de contrôle prédéfinis. Il ne doit pas être NULL.

*lpWindowName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null qui contient le nom de la fenêtre.

*dwStyle*<br/>
Spécifie les attributs de style de fenêtre. Pour obtenir une description des valeurs possibles, consultez [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [CWnd :: Create](../../mfc/reference/cwnd-class.md#create) .

*rect*<br/>
Taille et position de la fenêtre, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointe vers l’objet de fenêtre parente.

*nID*<br/>
Identificateur de la fenêtre enfant.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Les `CreateEx` paramètres spécifient le WNDCLASS, le style de fenêtre et (éventuellement) la position initiale et la taille de la fenêtre. `CreateEx`spécifie également le parent de la fenêtre (le cas échéant) et l’ID.

Lorsque `CreateEx` exécute, Windows envoie les messages [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)et [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) à la fenêtre.

Pour étendre la gestion des messages par défaut, dérivez une classe de `CMiniFrameWnd`, ajoutez une table des messages à la nouvelle classe et fournissez des fonctions membres pour les messages ci-dessus. Substituez `OnCreate`, par exemple, pour effectuer l’initialisation nécessaire pour une nouvelle classe.

Remplacer d’autres `On`gestionnaires de messages de *message* pour ajouter des fonctionnalités supplémentaires à votre classe dérivée.

Si le style WS_VISIBLE est donné, Windows envoie tous les messages requis pour activer et afficher la fenêtre. Si le style de fenêtre spécifie une barre de titre, le titre de la fenêtre pointé par le paramètre *lpszWindowName* est affiché dans la barre de titre.

Le paramètre *dwStyle* peut être n’importe quelle combinaison de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles).

Les anciennes fenêtres de la boîte à outils de la palette de style ne sont plus prises en charge. L’ancien style, qui n’avait pas de bouton de fermeture « X », était pris en charge lors de l’exécution d’une application MFC sur des versions antérieures de Windows, C++mais n’est plus pris en charge dans Visual .net. Seul le nouveau style WS_EX_TOOLWINDOW est désormais pris en charge. pour obtenir une description de ce style, consultez [styles de fenêtre étendus](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).

## <a name="see-also"></a>Voir aussi

[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)

---
title: CSpinButtonCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: c167745eed45b7081e62a2c3be225a33e7ee0520
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502442"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl, classe

Fournit les fonctionnalités du contrôle commun de bouton toupie (spin) Windows.

## <a name="syntax"></a>Syntaxe

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Construit un objet `CSpinButtonCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|Crée un contrôle spin Button et l’attache à un `CSpinButtonCtrl` objet.|
|[CSpinButtonCtrl::CreateEx](#createex)|Crée un contrôle de bouton toupie avec les styles étendus Windows spécifiés et l’attache `CSpinButtonCtrl` à un objet.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Récupère les informations d’accélération pour un contrôle de bouton toupie.|
|[CSpinButtonCtrl::GetBase](#getbase)|Récupère la base actuelle pour un contrôle de bouton toupie.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Récupère un pointeur vers la fenêtre associée actuelle.|
|[CSpinButtonCtrl::GetPos](#getpos)|Récupère la position actuelle d’un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::GetRange](#getrange)|Récupère les limites supérieure et inférieure (plage) pour un contrôle spin Button.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Définit l’accélération pour un contrôle de bouton toupie.|
|[CSpinButtonCtrl::SetBase](#setbase)|Définit la base pour un contrôle de bouton toupie.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Définit la fenêtre associée pour un contrôle de bouton toupie.|
|[CSpinButtonCtrl::SetPos](#setpos)|Définit la position actuelle du contrôle.|
|[CSpinButtonCtrl::SetRange](#setrange)|Définit les limites supérieure et inférieure (plage) pour un contrôle spin Button.|

## <a name="remarks"></a>Notes

Un «contrôle spin Button» (également appelé contrôle up-down) est une paire de boutons fléchés sur lesquels l’utilisateur peut cliquer pour incrémenter ou décrémenter une valeur, telle qu’une position de défilement ou un nombre affiché dans un contrôle auxiliaire. La valeur associée à un contrôle spin Button est appelée sa position actuelle. Le contrôle de bouton toupie est le plus souvent utilisé avec un contrôle compagnon, appelé «fenêtre associée».

Ce contrôle (et par conséquent `CSpinButtonCtrl` la classe) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT version 3,51 et versions ultérieures.

Pour l’utilisateur, un contrôle spin Button et sa fenêtre associée se présentent souvent comme un seul contrôle. Vous pouvez spécifier qu’un contrôle de bouton toupie se positionne automatiquement en regard de sa fenêtre associée, et qu’il affecte automatiquement à la légende de la fenêtre associée sa position actuelle. Vous pouvez utiliser un contrôle de bouton toupie avec un contrôle d’édition pour inviter l’utilisateur à entrer des données numériques.

Le fait de cliquer sur la flèche vers le haut déplace la position actuelle vers la valeur maximale et le fait de cliquer sur la flèche orientée vers le bas déplace la position actuelle vers la valeur minimale. Par défaut, la valeur minimale est 100 et la valeur maximale est 0. Chaque fois que le paramètre minimal est supérieur au paramètre maximal (par exemple, lorsque les paramètres par défaut sont utilisés), le fait de cliquer sur la flèche vers le haut diminue la valeur de la position et un clic sur la flèche vers le bas l’augmente.

Un contrôle de bouton toupie sans fenêtre associée fonctionne comme une sorte de barre de défilement simplifiée. Par exemple, un contrôle onglet affiche parfois un contrôle bouton toupie pour permettre à l’utilisateur de faire défiler des onglets supplémentaires dans l’affichage.

Pour plus d’informations sur `CSpinButtonCtrl`l’utilisation de, consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

Crée un contrôle toupie (spin Button) et l’attache `CSpinButtonCtrl` à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle spin Button. Applique une combinaison de styles de contrôle de bouton toupie au contrôle. Ces styles sont décrits dans les [styles de contrôle up-up](/windows/win32/Controls/up-down-control-styles) dans le SDK Windows.

*rect*<br/>
Spécifie la taille et la position du contrôle spin Button. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Pointeur vers la fenêtre parente du contrôle spin Button, généralement `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle spin Button.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’initialisation a réussi; Sinon, 0.

### <a name="remarks"></a>Notes

Vous devez d' `CSpinButtonCtrl` abord construire un objet en deux étapes, appeler le constructeur, puis `Create`appeler, ce qui crée le contrôle spin Button et l’attache à `CSpinButtonCtrl` l’objet.

Pour créer un contrôle de bouton toupie avec des styles de fenêtre étendus, appelez [CSpinButtonCtrl:: CreateEx](#createex) au lieu de `Create`.

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe à `CSpinButtonCtrl` l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle spin Button. Applique une combinaison de styles de contrôle de bouton toupie au contrôle. Ces styles sont décrits dans les [styles de contrôle up-up](/windows/win32/Controls/up-down-control-styles) dans le SDK Windows.

*rect*<br/>
Référence à une structure [Rect](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows WS_EX_.

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

Construit un objet `CSpinButtonCtrl`.

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

Récupère les informations d’accélération pour un contrôle de bouton toupie.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Paramètres

*nAccel*<br/>
Nombre d’éléments dans le tableau spécifié par *pAccel*.

*pAccel*<br/>
Pointeur vers un tableau de structures [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) qui reçoit des informations d’accélération.

### <a name="return-value"></a>Valeur de retour

Nombre de structures d’accélérateurs récupérées.

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

Récupère la base actuelle pour un contrôle de bouton toupie.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de base actuelle.

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

Récupère un pointeur vers la fenêtre associée actuelle.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre associée actuelle.

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

Récupère la position actuelle d’un contrôle de bouton toupie (spin).

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpbError*<br/>
Pointeur vers une valeur booléenne qui a la valeur zéro si la valeur est récupérée avec succès ou différente de zéro si une erreur se produit. Si ce paramètre a la valeur NULL, les erreurs ne sont pas signalées.

### <a name="return-value"></a>Valeur de retour

La première version retourne la position actuelle de 16 bits dans le mot de poids faible. Le mot de poids fort est différent de zéro si une erreur s’est produite.

La deuxième version retourne la position 32 bits.

### <a name="remarks"></a>Notes

Lorsqu’il traite la valeur retournée, le contrôle met à jour sa position actuelle en fonction de la légende de la fenêtre associée. Le contrôle retourne une erreur s’il n’y a aucune fenêtre associée ou si la légende spécifie une valeur non valide ou hors limites.

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

Récupère les limites supérieure et inférieure (plage) pour un contrôle spin Button.

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>Paramètres

*lower*<br/>
Référence à un entier qui reçoit la limite inférieure du contrôle.

*coin*<br/>
Référence à un entier qui reçoit la limite supérieure du contrôle.

### <a name="return-value"></a>Valeur de retour

La première version retourne une valeur 32 bits contenant les limites supérieure et inférieure. Le mot de poids faible est la limite supérieure du contrôle, et le mot de poids fort est la limite inférieure.

### <a name="remarks"></a>Notes

La fonction `GetRange32` membre récupère la plage du contrôle spin Button sous la forme d’un entier 32 bits.

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

Définit l’accélération pour un contrôle de bouton toupie.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Paramètres

*nAccel*<br/>
Nombre de structures [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) spécifiées par *pAccel*.

*pAccel*<br/>
Pointeur vers un tableau de structures UDACCEL qui contiennent des informations d’accélération. Les éléments doivent être triés dans l’ordre croissant en `nSec` fonction du membre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

Définit la base pour un contrôle de bouton toupie.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Paramètres

*nBase*<br/>
Nouvelle valeur de base pour le contrôle. Il peut être 10 pour Decimal ou 16 pour hexadécimal.

### <a name="return-value"></a>Valeur de retour

Valeur de base précédente en cas de réussite, ou zéro si une base non valide est spécifiée.

### <a name="remarks"></a>Notes

La valeur de base détermine si la fenêtre associée affiche des nombres en chiffres décimaux ou hexadécimaux. Les nombres hexadécimaux sont toujours non signés; les nombres décimaux sont signés.

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

Définit la fenêtre associée pour un contrôle de bouton toupie.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Paramètres

*pWndBuddy*<br/>
Pointeur vers la nouvelle fenêtre associée.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre associée précédente.

### <a name="remarks"></a>Notes

Un contrôle spin est presque toujours associé à une autre fenêtre, telle qu’un contrôle Edit, qui affiche du contenu. Cette autre fenêtre est appelée «copain» du contrôle spin.

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

Définit la position actuelle d’un contrôle de bouton toupie (spin).

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Nouvelle position pour le contrôle. Cette valeur doit être comprise dans la plage spécifiée par les limites supérieure et inférieure du contrôle.

### <a name="return-value"></a>Valeur de retour

Position précédente (précision de 16 bits pour `SetPos`, précision de 32 bits pour `SetPos32`).

### <a name="remarks"></a>Notes

`SetPos32`définit la position 32 bits.

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

Définit les limites supérieure et inférieure (plage) pour un contrôle spin Button.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Paramètres

*nLower* et *nUpper*<br/>
Limites supérieure et inférieure pour le contrôle. Pour `SetRange`, aucune limite ne peut être supérieure à UD_MAXVAL ou inférieure à UD_MINVAL; de plus, la différence entre les deux limites ne peut pas dépasser UD_MAXVAL. `SetRange32`n’impose aucune restriction sur les limites; Utilisez des entiers.

### <a name="remarks"></a>Notes

La fonction `SetRange32` membre définit la plage de bits 32 pour le contrôle spin Button.

> [!NOTE]
>  La plage par défaut pour le bouton toupie a la valeur maximale définie à zéro (0) et la valeur minimale à 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, le fait de cliquer sur la flèche vers le haut diminue la position et clique sur la flèche vers le bas pour l’augmenter. Utilisez `CSpinButtonCtrl::SetRange` pour ajuster ces valeurs.

## <a name="see-also"></a>Voir aussi

[Exemple MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl, classe](../../mfc/reference/csliderctrl-class.md)

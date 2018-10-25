---
title: CSpinButtonCtrl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5486b743d18f23e8bcd541ca956f6dd123182580
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083508"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl (classe)

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
|[CSpinButtonCtrl::Create](#create)|Crée un contrôle de bouton toupie (spin) et l’attache à un `CSpinButtonCtrl` objet.|
|[CSpinButtonCtrl::CreateEx](#createex)|Crée un contrôle de bouton toupie (spin) avec les styles étendus Windows spécifiés et l’attache à un `CSpinButtonCtrl` objet.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Récupère les informations d’accélération pour un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::GetBase](#getbase)|Extrait de la base d’un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Récupère un pointeur vers la fenêtre associée en cours.|
|[CSpinButtonCtrl::GetPos](#getpos)|Récupère la position actuelle d’un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::GetRange](#getrange)|Récupère les limites supérieures et inférieures (plage) d’un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Définit l’accélération pour un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::SetBase](#setbase)|Définit la base d’un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Définit la fenêtre associée pour un contrôle de bouton toupie (spin).|
|[CSpinButtonCtrl::SetPos](#setpos)|Définit la position actuelle pour le contrôle.|
|[CSpinButtonCtrl::SetRange](#setrange)|Définit les limites supérieures et inférieures (plage) d’un contrôle de bouton toupie (spin).|

## <a name="remarks"></a>Notes

Un « contrôle toupie » (également appelé contrôle up-down) est une paire de boutons fléchés que l’utilisateur peut cliquer pour incrémenter ou décrémenter une valeur, telle qu’une position de défilement ou un nombre affiché dans un contrôle Compagnon. La valeur associée à un contrôle de bouton toupie (spin) est appelée sa position actuelle. Un contrôle de bouton toupie (spin) est plus souvent utilisé avec un contrôle Compagnon, appelé « fenêtre associée ».

Ce contrôle (et par conséquent la `CSpinButtonCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT version 3.51 et ultérieures.

À l’utilisateur, un contrôle de bouton toupie (spin) et sa fenêtre associée souvent ressemblent à un seul contrôle. Vous pouvez spécifier qu’un contrôle de bouton toupie (spin) automatiquement se positionne à côté de sa fenêtre associée, et que la légende de la fenêtre associée automatiquement définie à sa position actuelle. Vous pouvez utiliser un contrôle de bouton toupie (spin) avec un contrôle d’édition pour inviter l’utilisateur pour entrée numérique.

En cliquant sur la flèche vers le haut déplace la position actuelle vers la valeur maximale, et en cliquant sur la flèche vers le bas déplace la position actuelle vers le minimum. Par défaut, la valeur minimale est de 100 et la valeur maximale est 0. Dès que la valeur minimale est supérieure au maximum (par exemple, lorsque les paramètres par défaut sont utilisés), en cliquant sur la baisse de flèche haut la valeur de position et en cliquant sur la flèche vers le bas pour l’augmenter.

Un contrôle de bouton toupie (spin) sans fenêtre associée fonctionne comme une sorte de barre de défilement simplifiée. Par exemple, un contrôle onglet affiche parfois un contrôle de bouton toupie (spin) pour permettre aux utilisateurs de faire défiler des onglets supplémentaires dans l’affichage.

Pour plus d’informations sur l’utilisation de `CSpinButtonCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

Crée un contrôle de bouton toupie (spin) et l’attache à un `CSpinButtonCtrl` objet...

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle de bouton toupie (spin). Appliquer n’importe quelle combinaison de styles de contrôle de bouton toupie (spin) au contrôle. Ces styles sont décrites dans [Styles de contrôle Up-Down](/windows/desktop/Controls/up-down-control-styles) dans le SDK Windows.

*Rect*<br/>
Spécifie la taille et la position du contrôle de bouton toupie (spin). Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure

*pParentWnd*<br/>
Un pointeur vers la fenêtre de parent du contrôle de bouton toupie (spin), généralement un `CDialog`. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de bouton toupie (spin)

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’initialisation a abouti ; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CSpinButtonCtrl` tout d’abord l’objet en deux étapes, appelez le constructeur, puis appelez `Create`, ce qui crée le contrôle de bouton toupie (spin) et l’attache à la `CSpinButtonCtrl` objet.

Pour créer un contrôle de bouton toupie (spin) avec les styles de fenêtre étendus, appelez [CSpinButtonCtrl::CreateEx](#createex) au lieu de `Create`.

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) et l’associe le `CSpinButtonCtrl` objet.

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
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle de bouton toupie (spin). Appliquer n’importe quelle combinaison de styles de contrôle de bouton toupie (spin) au contrôle. Ces styles sont décrites dans [Styles de contrôle Up-Down](/windows/desktop/Controls/up-down-control-styles) dans le SDK Windows.

*Rect*<br/>
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows WS_EX_.

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

Construit un objet `CSpinButtonCtrl`.

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

Récupère les informations d’accélération pour un contrôle de bouton toupie (spin).

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Paramètres

*nAccel*<br/>
Nombre d’éléments dans le tableau spécifié par *pAccel*.

*pAccel*<br/>
Pointeur vers un tableau de [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) structures qui reçoit les informations de l’accélération.

### <a name="return-value"></a>Valeur de retour

Nombre de structures d’accélérateur récupérés.

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

Extrait de la base d’un contrôle de bouton toupie (spin).

```
UINT GetBase() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de base en cours.

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

Récupère un pointeur vers la fenêtre associée en cours.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre associée en cours.

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

Récupère la position actuelle d’un contrôle de bouton toupie (spin).

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpbError*<br/>
Un pointeur vers une valeur booléenne qui est définie sur zéro si la valeur est récupérée et non nulle si une erreur se produit. Si ce paramètre est défini avec la valeur NULL, les erreurs ne sont pas signalées.

### <a name="return-value"></a>Valeur de retour

La première version retourne la position actuelle de 16 bits dans le mot de poids faible. Le mot de poids fort est différent de zéro si une erreur s’est produite.

La deuxième version retourne la position de 32 bits.

### <a name="remarks"></a>Notes

Lorsqu’il traite la valeur retournée, le contrôle met à jour sa position actuelle en fonction de la légende de la fenêtre associée. Le contrôle retourne une erreur s’il n’existe aucune fenêtre associée ou si la légende spécifie une valeur non valide ou hors limites.

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

Récupère les limites supérieures et inférieures (plage) d’un contrôle de bouton toupie (spin).

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

*inférieur*<br/>
Référence à un entier qui reçoit la limite inférieure pour le contrôle.

*supérieur*<br/>
Référence à un entier qui reçoit la limite supérieure pour le contrôle.

### <a name="return-value"></a>Valeur de retour

La première version retourne une valeur de 32 bits qui contient les limites supérieures et inférieures. Le mot de poids faible est la limite supérieure pour le contrôle et le mot de poids fort est la limite inférieure.

### <a name="remarks"></a>Notes

La fonction membre `GetRange32` récupère la plage du contrôle de bouton toupie (spin) comme un entier 32 bits.

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

Définit l’accélération pour un contrôle de bouton toupie (spin).

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Paramètres

*nAccel*<br/>
Nombre de [UDACCEL](/windows/desktop/api/commctrl/ns-commctrl-_udaccel) structures spécifié par *pAccel*.

*pAccel*<br/>
Pointeur vers un tableau de structures UDACCEL, qui contiennent des informations de l’accélération. Les éléments doivent être triés dans l’ordre croissant selon la `nSec` membre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

Définit la base d’un contrôle de bouton toupie (spin).

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Paramètres

*nBase*<br/>
Nouvelle valeur de base pour le contrôle. Il peut être de 10 pour les décimales ou 16 pour les nombres hexadécimaux.

### <a name="return-value"></a>Valeur de retour

La valeur de base précédente en cas de réussite, ou zéro si une base non valide est fournie.

### <a name="remarks"></a>Notes

La valeur de base détermine si la fenêtre associée affiche les nombres sous forme décimale ou hexadécimale. Nombres hexadécimaux sont toujours non signés ; nombres décimaux sont signés.

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

Définit la fenêtre associée pour un contrôle de bouton toupie (spin).

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Paramètres

*pWndBuddy*<br/>
Pointeur vers la nouvelle fenêtre associée.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre associée précédente.

### <a name="remarks"></a>Notes

Un contrôle spin est presque toujours associé à une autre fenêtre, par exemple un contrôle d’édition, qui affiche du contenu. Autres cette fenêtre est appelée « buddy » du contrôle spin.

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

Définit la position actuelle pour un contrôle de bouton toupie (spin).

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Paramètres

*nPos*<br/>
Nouvelle position du contrôle. Cette valeur doit être dans la plage spécifiée par les limites supérieures et inférieures pour le contrôle.

### <a name="return-value"></a>Valeur de retour

La position précédente (précision 16 bits pour `SetPos`, 32 bits précision pour `SetPos32`).

### <a name="remarks"></a>Notes

`SetPos32` définit la position de 32 bits.

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

Définit les limites supérieures et inférieures (plage) d’un contrôle de bouton toupie (spin).

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
Limites supérieure et inférieure pour le contrôle. Pour `SetRange`, aucune limite peut être supérieur à UD_MAXVAL ou inférieure à UD_MINVAL ; en outre, la différence entre les deux limites ne doit pas dépasser UD_MAXVAL. `SetRange32` n’impose aucune restriction sur les limites ; utiliser des entiers.

### <a name="remarks"></a>Notes

La fonction membre `SetRange32` définit la plage de 32 bits pour le contrôle de bouton toupie (spin).

> [!NOTE]
>  La plage par défaut pour le bouton toupie (spin) a la valeur maximale définie sur zéro (0) et la valeur minimale définie à 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, en cliquant sur la flèche vers le haut diminue la position et en cliquant sur la flèche vers le bas il augmente. Utilisez `CSpinButtonCtrl::SetRange` pour ajuster ces valeurs.

## <a name="see-also"></a>Voir aussi

[MFC exemple CMNCTRL2](../../visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl, classe](../../mfc/reference/csliderctrl-class.md)

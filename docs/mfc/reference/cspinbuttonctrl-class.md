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
ms.openlocfilehash: 4230d43bad8bcc15bcb26aaf0357e70216909ba1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318127"
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
|[CSpinButtonCtrl::Créer](#create)|Crée un contrôle de bouton de `CSpinButtonCtrl` rotation et le fixe à un objet.|
|[CSpinButtonCtrl::CreateEx](#createex)|Crée un contrôle de bouton de rotation avec les `CSpinButtonCtrl` styles Windows étendus spécifiés et le fixe à un objet.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Récupère les informations d’accélération pour un contrôle de bouton de rotation.|
|[CSpinButtonCtrl::GetBase](#getbase)|Récupère la base actuelle pour un contrôle de bouton de rotation.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Récupère un pointeur à la fenêtre de copain actuel.|
|[CSpinButtonCtrl::GetPos](#getpos)|Récupère la position actuelle d’un bouton de rotation.|
|[CSpinButtonCtrl::GetRange](#getrange)|Récupère les limites supérieures et inférieures (gamme) pour un contrôle de bouton de rotation.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Définit l’accélération pour un contrôle de bouton de rotation.|
|[CSpinButtonCtrl::SetBase](#setbase)|Définit la base pour un contrôle de bouton de rotation.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Définit la fenêtre de copain pour un contrôle de bouton de rotation.|
|[CSpinButtonCtrl::SetPos](#setpos)|Définit la position actuelle pour le contrôle.|
|[CSpinButtonCtrl::SetRange](#setrange)|Définit les limites supérieures et inférieures (portée) pour un contrôle de bouton de rotation.|

## <a name="remarks"></a>Notes

Un « contrôle du bouton de rotation » (également connu sous le nom de contrôle vers le bas) est une paire de boutons de flèche que l’utilisateur peut cliquer pour incrémenter ou décrfecter une valeur, telle qu’une position de défilement ou un numéro affiché dans un contrôle de compagnon. La valeur associée à un contrôle de bouton de rotation est appelée sa position actuelle. Un contrôle de bouton de rotation est le plus souvent utilisé avec un contrôle de compagnon, appelé une « fenêtre de copain. »

Ce contrôle (et `CSpinButtonCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT version 3.51 et plus tard.

Pour l’utilisateur, un contrôle de bouton de spin et sa fenêtre de copain ressemblent souvent à un seul contrôle. Vous pouvez spécifier qu’un bouton de rotation se positionne automatiquement à côté de sa fenêtre de copain, et qu’il régle automatiquement la légende de la fenêtre de copain à sa position actuelle. Vous pouvez utiliser un contrôle de bouton de rotation avec un contrôle de modification pour inciter l’utilisateur à l’entrée numérique.

En cliquant sur la flèche vers le haut se déplace la position actuelle vers le maximum, et en cliquant sur la flèche vers le bas déplace la position actuelle vers le minimum. Par défaut, le minimum est de 100 et le maximum est de 0. Chaque fois que le paramètre minimum est supérieur au paramètre maximum (par exemple, lorsque les paramètres par défaut sont utilisés), en cliquant sur la flèche vers le haut diminue la valeur de position et en cliquant sur la flèche vers le bas augmente.

Un contrôle de bouton de rotation sans une fenêtre de copain fonctionne comme une sorte de barre de défilement simplifiée. Par exemple, un contrôle d’onglet affiche parfois un contrôle de bouton de rotation pour permettre à l’utilisateur de faire défiler des onglets supplémentaires en vue.

Pour plus d’informations sur l’utilisation `CSpinButtonCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation [CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Créer

Crée un contrôle de bouton de `CSpinButtonCtrl` rotation et le fixe à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du bouton de rotation. Appliquez n’importe quelle combinaison de styles de commande de bouton de rotation au contrôle. Ces styles sont décrits dans [Up-Down Control Styles](/windows/win32/Controls/up-down-control-styles) dans le Windows SDK.

*Rect*<br/>
Spécifie la taille et la position du bouton de rotation. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Un pointeur à la fenêtre parente `CDialog`du bouton de rotation, habituellement un . Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du bouton de rotation.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CSpinButtonCtrl` objet en deux étapes d’abord, appelez le constructeur, puis appelez, `Create`ce qui crée le contrôle du bouton de rotation et le fixe à l’objet. `CSpinButtonCtrl`

Pour créer un contrôle de bouton de spin avec des styles de fenêtre `Create`étendus, appelez [CSpinButtonCtrl::CreateEx](#createex) au lieu de .

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx

Crée un contrôle (une fenêtre enfant) `CSpinButtonCtrl` et l’associe à l’objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Spécifie le style du bouton de rotation. Appliquez n’importe quelle combinaison de styles de commande de bouton de rotation au contrôle. Ces styles sont décrits dans [Up-Down Control Styles](/windows/win32/Controls/up-down-control-styles) dans le Windows SDK.

*Rect*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows WS_EX_.

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl

Construit un objet `CSpinButtonCtrl`.

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel

Récupère les informations d’accélération pour un contrôle de bouton de rotation.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Paramètres

*nAccel (en)*<br/>
Nombre d’éléments dans le tableau spécifié par *pAccel*.

*pAccel (en)*<br/>
Pointeur vers un tableau de structures [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) qui reçoit des informations d’accélération.

### <a name="return-value"></a>Valeur de retour

Nombre de structures d’accélérateur récupérées.

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase

Récupère la base actuelle pour un contrôle de bouton de rotation.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur de base actuelle.

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy

Récupère un pointeur à la fenêtre de copain actuel.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre de copain actuel.

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos

Récupère la position actuelle d’un bouton de rotation.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpbError*<br/>
Un pointeur à une valeur boolean qui est réglé à zéro si la valeur est récupérée avec succès ou non-zéro si une erreur se produit. Si ce paramètre est défini à NULL, les erreurs ne sont pas signalées.

### <a name="return-value"></a>Valeur de retour

La première version renvoie la position actuelle 16 bits dans le mot de bas ordre. Le mot de haute commande est nonzero si une erreur s’est produite.

La deuxième version renvoie la position 32 bits.

### <a name="remarks"></a>Notes

Lorsqu’il traite la valeur retournée, le contrôle met à jour sa position actuelle en fonction de la légende de la fenêtre de copain. Le contrôle renvoie une erreur s’il n’y a pas de fenêtre de copain ou si la légende spécifie une valeur invalide ou hors de gamme.

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl::GetRange

Récupère les limites supérieures et inférieures (gamme) pour un contrôle de bouton de rotation.

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

*Inférieur*<br/>
Référence à un intégrant qui reçoit la limite inférieure pour le contrôle.

*Supérieur*<br/>
Référence à un intégrant qui reçoit la limite supérieure pour le contrôle.

### <a name="return-value"></a>Valeur de retour

La première version renvoie une valeur 32 bits contenant les limites supérieures et inférieures. Le mot de bas ordre est la limite supérieure pour le contrôle, et le mot de haut ordre est la limite inférieure.

### <a name="remarks"></a>Notes

La fonction `GetRange32` membre récupère la portée du bouton de rotation en tant qu’intégrant 32 bits.

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonCtrl::SetAccel

Définit l’accélération pour un contrôle de bouton de rotation.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Paramètres

*nAccel (en)*<br/>
Nombre de structures [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) spécifiées par *pAccel*.

*pAccel (en)*<br/>
Pointeur vers un tableau de structures UDACCEL, qui contiennent des informations d’accélération. Les éléments doivent être triés dans `nSec` l’ordre ascendant en fonction du membre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonCtrl::SetBase

Définit la base pour un contrôle de bouton de rotation.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Paramètres

*nBase (en)*<br/>
Nouvelle valeur de base pour le contrôle. Il peut être de 10 pour décimale ou 16 pour hexadecimal.

### <a name="return-value"></a>Valeur de retour

La valeur de base précédente en cas de succès, ou zéro si une base invalide est donnée.

### <a name="remarks"></a>Notes

La valeur de base détermine si la fenêtre de copain affiche des nombres en chiffres décimales ou hexadecimal. Les nombres hexadecimals ne sont toujours pas signés; nombres décimaux sont signés.

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy

Définit la fenêtre de copain pour un contrôle de bouton de rotation.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Paramètres

*pWndBuddy*<br/>
Pointeur vers la nouvelle fenêtre de copain.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre de copain précédent.

### <a name="remarks"></a>Notes

Un contrôle de rotation est presque toujours associé à une autre fenêtre, comme un contrôle de modification, qui affiche un certain contenu. Cette autre fenêtre est appelée le "copain" du contrôle de spin.

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonCtrl::SetPos

Définit la position actuelle pour un contrôle de bouton de rotation.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Paramètres

*Osbl*<br/>
Nouvelle position pour le contrôle. Cette valeur doit être dans la plage spécifiée par les limites supérieures et inférieures pour le contrôle.

### <a name="return-value"></a>Valeur de retour

La position précédente (16 `SetPos`bits de précision pour `SetPos32`, 32 bits de précision pour ).

### <a name="remarks"></a>Notes

`SetPos32`définit la position 32 bits.

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonCtrl::SetRange

Définit les limites supérieures et inférieures (portée) pour un contrôle de bouton de rotation.

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
Limites supérieures et inférieures pour le contrôle. Car, `SetRange`ni l’une ni l’autre limite ne peut être supérieure à UD_MAXVAL ou moins de UD_MINVAL; en outre, la différence entre les deux limites ne peut excéder UD_MAXVAL. `SetRange32`ne impose aucune restriction aux limites; utiliser desintégrants.

### <a name="remarks"></a>Notes

La fonction `SetRange32` membre définit la plage 32 bits pour le contrôle du bouton de rotation.

> [!NOTE]
> La plage par défaut pour le bouton de rotation a le maximum défini à zéro (0) et le minimum réglé à 100. Étant donné que la valeur maximale est inférieure à la valeur minimale, en cliquant sur la flèche vers le haut diminuera la position et en cliquant sur la flèche vers le bas l’augmentera. Utilisez `CSpinButtonCtrl::SetRange` pour ajuster ces valeurs.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CSliderCtrl](../../mfc/reference/csliderctrl-class.md)

---
title: CHotKeyCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: a79cc0ab2c01633f96430477aa536a60385461e9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750802"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl, classe

Fournit les fonctionnalités du contrôle commun de touche d'accès rapide Windows.

## <a name="syntax"></a>Syntaxe

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Construit un objet `CHotKeyCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHotKeyCtrl::Créer](#create)|Crée un contrôle de clé chaud `CHotKeyCtrl` et l’attache à un objet.|
|[CHotKeyCtrl::CreateEx](#createex)|Crée un contrôle de clé chaude avec les styles `CHotKeyCtrl` windows étendus spécifiés et le fixe à un objet.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Récupère le code clé virtuel et les indicateurs modificateurs d’une clé chaude à partir d’un contrôle de clé chaud.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Récupère le nom clé, dans l’ensemble de caractères local, attribué à une clé chaude.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Récupère le nom clé, dans l’ensemble de caractères local, attribué au code clé virtuel spécifié.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Définit la combinaison de clés chaudes pour un contrôle de clé chaud.|
|[CHotKeyCtrl::SetRules](#setrules)|Définit les combinaisons invalides et la combinaison de modificateur par défaut pour un contrôle de clé chaud.|

## <a name="remarks"></a>Notes

Un « contrôle de clé chaude » est une fenêtre qui permet à l’utilisateur de créer une clé chaude. Une « clé chaude » est une combinaison clé que l’utilisateur peut appuyer pour effectuer une action rapidement. (Par exemple, un utilisateur peut créer une clé chaude qui active une fenêtre donnée et l’amène au sommet de la commande Z.) Le contrôle des clés chaudes affiche les choix de l’utilisateur et garantit que l’utilisateur sélectionne une combinaison de clés valide.

Ce contrôle (et `CHotKeyCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT version 3.51 et plus tard.

Lorsque l’utilisateur a choisi une combinaison de clés, l’application peut récupérer la combinaison de clés spécifiée à partir du contrôle et utiliser le message WM_SETHOTKEY pour configurer la clé chaude dans le système. Chaque fois que l’utilisateur appuie la clé chaude par la suite, de n’importe quelle partie du système, la fenêtre spécifiée dans le message WM_SETHOTKEY reçoit un message WM_SYSCOMMAND spécifiant SC_HOTKEY. Ce message active la fenêtre qui la reçoit. La clé chaude reste valide jusqu’à ce que l’application qui a appelé WM_SETHOTKEY quitte.

Ce mécanisme est différent du support clé chaud qui dépend du message WM_HOTKEY et des fonctions Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) et [UnregisterHotKey.](/windows/win32/api/winuser/nf-winuser-unregisterhotkey)

Pour plus d’informations sur l’utilisation `CHotKeyCtrl`, voir [Contrôles](../../mfc/controls-mfc.md) et Utilisation de [CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a>CHotKeyCtrl::CHotKeyCtrl

Construit un objet `CHotKeyCtrl`.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a>CHotKeyCtrl::Créer

Crée un contrôle de clé chaud `CHotKeyCtrl` et l’attache à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Spécifie le style du contrôle des clés chaudes. Appliquer n’importe quelle combinaison de styles de contrôle. Voir [Les styles de contrôle commun](/windows/win32/Controls/common-control-styles) dans le SDK Windows pour plus d’informations.

*Rect*<br/>
Spécifie la taille et la position du contrôle des clés chaudes. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une [structure RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle de la clé chaude, habituellement un [CDialog](../../mfc/reference/cdialog-class.md). Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de la clé chaude.

### <a name="return-value"></a>Valeur de retour

Nonzero, si l’initialisation a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CHotKeyCtrl` objet en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , ce `CHotKeyCtrl` qui crée le contrôle de la clé chaude et le fixe à l’objet.

Si vous souhaitez utiliser des styles windows étendus `Create`avec votre contrôle, appelez [CreateEx](#createex) au lieu de .

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a>CHotKeyCtrl::CreateEx

Appelez cette fonction pour créer un contrôle (une `CHotKeyCtrl` fenêtre enfant) et l’associer à l’objet.

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
Spécifie le style étendu du contrôle en cours de création. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Spécifie le style du contrôle des clés chaudes. Appliquer n’importe quelle combinaison de styles de contrôle. Pour plus d’informations, voir [Styles de contrôle commun](/windows/win32/Controls/common-control-styles) dans le SDK Windows.

*Rect*<br/>
Une référence à une structure [RECT](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a>CHotKeyCtrl::GetHotKey

Récupère le code de clé virtuel et les indicateurs modificateurs d’un raccourci clavier à partir d’un contrôle de clé à chaud.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Paramètres

*wVirtualKeyCode (en anglais seulement)*<br/>
[out] Code clé virtuel du raccourci clavier. Pour une liste de codes clés virtuels standard, voir Winuser.h.

*wModifiers (en)*<br/>
[out] Une combinaison bitwise (OU) de drapeaux qui indiquent les touches modificateur dans le raccourci clavier.

Les drapeaux modificateurs sont les suivants :

|Indicateur|Clé correspondante|
|----------|-----------------------|
|HOTKEYF_ALT|touche ALT|
|HOTKEYF_CONTROL|Clé CTRL|
|HOTKEYF_EXT|Clé étendue|
|HOTKEYF_SHIFT|Clé SHIFT|

### <a name="return-value"></a>Valeur de retour

Dans la première méthode surchargée, un DWORD qui contient le code clé virtuel et les indicateurs modificateurs. Le byte de faible ordre du mot de bas ordre contient le code clé virtuel, le byte de haute commande du mot de bas ordre contient les drapeaux modificateur, et le mot de haut ordre est nul.

### <a name="remarks"></a>Notes

Le code clé virtuel et les touches modificateurs définissent ensemble le raccourci clavier.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a>CHotKeyCtrl::GetHotKeyName

Appelez cette fonction de membre pour obtenir le nom localisé de la clé chaude.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom localisé de la clé chaude actuellement sélectionnée. S’il n’y `GetHotKeyName` a pas de clé chaude sélectionnée, renvoie une chaîne vide.

### <a name="remarks"></a>Notes

Le nom que cette fonction de membre retourne vient du conducteur du clavier. Vous pouvez installer un conducteur de clavier non localisé dans une version localisée de Windows, et vice versa.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a>CHotKeyCtrl::GetKeyName

Appelez cette fonction de membre pour obtenir le nom localisé de la clé assignée à un code clé virtuel spécifié.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Paramètres

*Vk*<br/>
Le code clé virtuel.

*fExtended*<br/>
Si le code clé virtuel est une clé étendue, TRUE; autrement FALSE.

### <a name="return-value"></a>Valeur de retour

Le nom localisé de la clé spécifiée par le paramètre *vk.* Si la clé n’a `GetKeyName` pas de nom cartographié, renvoie une chaîne vide.

### <a name="remarks"></a>Notes

Le nom clé que cette fonction retourne vient du conducteur du clavier, de sorte que vous pouvez installer un conducteur de clavier non localisé dans une version localisée de Windows, et vice versa.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a>CHotKeyCtrl::SetHotKey

Définit le raccourci clavier pour un contrôle de clé chaud.

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Paramètres

*wVirtualKeyCode (en anglais seulement)*<br/>
[dans] Code clé virtuel du raccourci clavier. Pour une liste de codes clés virtuels standard, voir Winuser.h.

*wModifiers (en)*<br/>
[dans] Une combinaison bitwise (OU) de drapeaux qui indiquent les touches modificateur dans le raccourci clavier.

Les drapeaux modificateurs sont les suivants :

|Indicateur|Clé correspondante|
|----------|-----------------------|
|HOTKEYF_ALT|touche ALT|
|HOTKEYF_CONTROL|Clé CTRL|
|HOTKEYF_EXT|Clé étendue|
|HOTKEYF_SHIFT|Clé SHIFT|

### <a name="remarks"></a>Notes

Le code clé virtuel et les touches modificateurs définissent ensemble le raccourci clavier.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a>CHotKeyCtrl::SetRules

Appelez cette fonction pour définir les combinaisons invalides et la combinaison de modificateur par défaut pour un contrôle de clé chaud.

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Paramètres

*wInvalidComb (en)*<br/>
Array de drapeaux qui spécifient des combinaisons de clés invalides. Il peut s’agir d’une combinaison des valeurs suivantes :

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL-ALT

- HKCOMB_NONE clés non modifiées

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT-ALT

- HKCOMB_SC SHIFT-CTRL

- HKCOMB_SCA SHIFT-CTRL-ALT

*wModifiers (en)*<br/>
Array de drapeaux qui spécifie la combinaison de clés à utiliser lorsque l’utilisateur entre dans une combinaison invalide. Pour plus d’informations sur les indicateurs modificateurs, voir [GetHotKey](#gethotkey).

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur entre dans une combinaison de clés invalides, telle que définie par des drapeaux spécifiés dans *wInvalidComb*, le système utilise l’opérateur DE LAR pour combiner les clés saisies par l’utilisateur avec les drapeaux spécifiés dans *wModifiers*. La combinaison de clés qui en résulte est convertie en chaîne, puis affichée dans le contrôle de la clé chaude.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

---
description: 'En savoir plus sur : classe CHotKeyCtrl'
title: CHotKeyCtrl (classe)
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
ms.openlocfilehash: 875b35c2c683cc8502c1bc2668aad5b4a0326757
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331775"
---
# <a name="chotkeyctrl-class"></a>CHotKeyCtrl (classe)

Fournit les fonctionnalités du contrôle commun de touche d'accès rapide Windows.

## <a name="syntax"></a>Syntaxe

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CHotKeyCtrl :: CHotKeyCtrl](#chotkeyctrl)|Construit un objet `CHotKeyCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHotKeyCtrl :: Create](#create)|Crée un contrôle de touche d’accès rapide et l’attache à un `CHotKeyCtrl` objet.|
|[CHotKeyCtrl :: CreateEx](#createex)|Crée un contrôle de touche d’accès rapide avec les styles étendus Windows spécifiés et l’attache à un `CHotKeyCtrl` objet.|
|[CHotKeyCtrl :: GetHotKey](#gethotkey)|Récupère le code de touche virtuel et les indicateurs de modificateur d’une touche d’accès rapide à partir d’un contrôle de touche d’accès rapide.|
|[CHotKeyCtrl :: GetHotKeyName](#gethotkeyname)|Récupère le nom de clé, dans le jeu de caractères local, affecté à une touche d’accès rapide.|
|[CHotKeyCtrl :: GetKeyName](#getkeyname)|Récupère le nom de clé, dans le jeu de caractères local, affecté au code de touche virtuelle spécifié.|
|[CHotKeyCtrl :: SetHotKey](#sethotkey)|Définit la combinaison de touches d’accès rapide pour un contrôle de touche d’accès rapide.|
|[CHotKeyCtrl :: SetRules](#setrules)|Définit les combinaisons non valides et la combinaison de modificateur par défaut pour un contrôle de touche d’accès rapide.|

## <a name="remarks"></a>Notes

Un « contrôle de touche d’accès rapide » est une fenêtre qui permet à l’utilisateur de créer une touche d’accès rapide. Une « touche d’accès rapide » est une combinaison de touches que l’utilisateur peut appuyer pour effectuer une action rapidement. (Par exemple, un utilisateur peut créer une touche d’accès rapide qui active une fenêtre donnée et l’affiche en haut de l’ordre Z.) Le contrôle de touche d’accès rapide affiche les choix de l’utilisateur et s’assure que l’utilisateur sélectionne une combinaison de touches valide.

Ce contrôle (et par conséquent la `CHotKeyCtrl` classe) est uniquement disponible pour les programmes qui s’exécutent sous windows 95/98 et Windows NT version 3,51 et versions ultérieures.

Lorsque l’utilisateur a choisi une combinaison de touches, l’application peut récupérer la combinaison de touches spécifiée à partir du contrôle et utiliser le message WM_SETHOTKEY pour configurer la touche d’accès rapide dans le système. Chaque fois que l’utilisateur appuie sur la touche d’accès rapide par la suite, à partir de n’importe quelle partie du système, la fenêtre spécifiée dans le message de WM_SETHOTKEY reçoit un message WM_SYSCOMMAND spécifiant SC_HOTKEY. Ce message active la fenêtre qui le reçoit. La touche d’accès rapide reste valide jusqu’à ce que l’application qui a appelé WM_SETHOTKEY se termine.

Ce mécanisme est différent de la prise en charge de la touche d’accès rapide qui dépend du message WM_HOTKEY et des fonctions Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) et [UnregisterHotKey](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) .

Pour plus d’informations sur l’utilisation de `CHotKeyCtrl` , consultez [contrôles](../../mfc/controls-mfc.md) et [utilisation de CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a> CHotKeyCtrl :: CHotKeyCtrl

Construit un objet `CHotKeyCtrl`.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a> CHotKeyCtrl :: Create

Crée un contrôle de touche d’accès rapide et l’attache à un `CHotKeyCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Spécifie le style du contrôle de touche d’accès rapide. Appliquez une combinaison de styles de contrôle. Pour plus d’informations, consultez [styles de contrôle courants](/windows/win32/Controls/common-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle de touche d’accès rapide. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une [structure Rect](/windows/win32/api/windef/ns-windef-rect).

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle de touche d’accès rapide, généralement un [CDialog](../../mfc/reference/cdialog-class.md). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de touche d’accès rapide.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’initialisation a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CHotKeyCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create` , qui crée le contrôle de touche d’accès rapide et l’attache à l' `CHotKeyCtrl` objet.

Si vous souhaitez utiliser des styles Windows étendus avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create` .

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a> CHotKeyCtrl :: CreateEx

Appelez cette fonction pour créer un contrôle (une fenêtre enfant) et l’associer à l' `CHotKeyCtrl` objet.

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
Spécifie le style du contrôle de touche d’accès rapide. Appliquez une combinaison de styles de contrôle. Pour plus d’informations, consultez [styles de contrôle communs](/windows/win32/Controls/common-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) décrivant la taille et la position de la fenêtre à créer, en coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de la fenêtre enfant du contrôle.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des styles Windows étendus, spécifiés par la préversion de style étendu Windows **WS_EX_**.

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a> CHotKeyCtrl :: GetHotKey

Récupère le code de touche virtuel et les indicateurs de modificateur d’un raccourci clavier à partir d’un contrôle de touche d’accès rapide.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Paramètres

*wVirtualKeyCode*<br/>
à Code de la touche virtuelle du raccourci clavier. Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h.

*wModifiers*<br/>
à Combinaison d’opérations de bits d’indicateurs qui indiquent les touches de modification du raccourci clavier.

Les indicateurs de modificateur sont les suivants :

|Indicateur|Clé correspondante|
|----------|-----------------------|
|HOTKEYF_ALT|touche ALT|
|HOTKEYF_CONTROL|Touche CTRL|
|HOTKEYF_EXT|Clé étendue|
|HOTKEYF_SHIFT|Touche Maj|

### <a name="return-value"></a>Valeur renvoyée

Dans la première méthode surchargée, valeur DWORD qui contient le code de touche virtuelle et les indicateurs de modificateur. L’octet de poids faible du mot de poids faible contient le code de touche virtuelle, l’octet de poids fort du mot de poids faible contient les indicateurs de modificateur et le mot de poids fort est égal à zéro.

### <a name="remarks"></a>Notes

Le code de la touche virtuelle et les touches de modification définissent ensemble le raccourci clavier.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a> CHotKeyCtrl :: GetHotKeyName

Appelez cette fonction membre pour récupérer le nom localisé de la touche d’accès rapide.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nom localisé de la touche d’accès rapide sélectionnée. Si aucune touche d’accès rapide n’est sélectionnée, `GetHotKeyName` retourne une chaîne vide.

### <a name="remarks"></a>Notes

Le nom retourné par cette fonction membre provient du pilote de clavier. Vous pouvez installer un pilote de clavier non localisé dans une version localisée de Windows, et vice versa.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a> CHotKeyCtrl :: GetKeyName

Appelez cette fonction membre pour obtenir le nom localisé de la clé assignée à un code de clé virtuelle spécifié.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Paramètres

*VK*<br/>
Code de la touche virtuelle.

*fExtended*<br/>
Si le code de la touche virtuelle est une clé étendue, TRUE ; Sinon, FALSe.

### <a name="return-value"></a>Valeur renvoyée

Nom localisé de la clé spécifiée par le paramètre *VK* . Si la clé n’a pas de nom mappé, `GetKeyName` retourne une chaîne vide.

### <a name="remarks"></a>Notes

Le nom de clé renvoyé par cette fonction provient du pilote de clavier, ce qui vous permet d’installer un pilote de clavier non localisé dans une version localisée de Windows, et vice versa.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a> CHotKeyCtrl :: SetHotKey

Définit le raccourci clavier pour un contrôle de touche d’accès rapide.

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Paramètres

*wVirtualKeyCode*<br/>
dans Code de la touche virtuelle du raccourci clavier. Pour obtenir la liste des codes de touches virtuelles standard, consultez Winuser. h.

*wModifiers*<br/>
dans Combinaison d’opérations de bits d’indicateurs qui indiquent les touches de modification du raccourci clavier.

Les indicateurs de modificateur sont les suivants :

|Indicateur|Clé correspondante|
|----------|-----------------------|
|HOTKEYF_ALT|touche ALT|
|HOTKEYF_CONTROL|Touche CTRL|
|HOTKEYF_EXT|Clé étendue|
|HOTKEYF_SHIFT|Touche Maj|

### <a name="remarks"></a>Notes

Le code de la touche virtuelle et les touches de modification définissent ensemble le raccourci clavier.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a> CHotKeyCtrl :: SetRules

Appelez cette fonction pour définir les combinaisons non valides et la combinaison de modificateurs par défaut pour un contrôle de touche d’accès rapide.

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Paramètres

*wInvalidComb*<br/>
Tableau d’indicateurs qui spécifie des combinaisons de touches non valides. Il peut s’agir d’une combinaison des valeurs suivantes :

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE les clés non modifiées

- HKCOMB_S MAJ

- HKCOMB_SA MAJ + ALT

- HKCOMB_SC MAJ + CTRL

- HKCOMB_SCA MAJ + CTRL + ALT

*wModifiers*<br/>
Tableau d’indicateurs qui spécifie la combinaison de touches à utiliser lorsque l’utilisateur entre une combinaison non valide. Pour plus d’informations sur les indicateurs de modificateur, consultez [GetHotKey](#gethotkey).

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur entre une combinaison de touches non valide, comme défini par les indicateurs spécifiés dans *wInvalidComb*, le système utilise l’opérateur or pour combiner les clés entrées par l’utilisateur avec les indicateurs spécifiés dans *wModifiers*. La combinaison de touches obtenue est convertie en chaîne, puis affichée dans le contrôle de touche d’accès rapide.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

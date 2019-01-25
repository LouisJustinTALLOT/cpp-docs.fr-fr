---
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
ms.openlocfilehash: 0b673c873f773844c13894d3f0448536f297dc53
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894508"
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
|[CHotKeyCtrl::CHotKeyCtrl](#chotkeyctrl)|Construit un objet `CHotKeyCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CHotKeyCtrl::Create](#create)|Crée un contrôle de touche d’accès rapide et l’attache à un `CHotKeyCtrl` objet.|
|[CHotKeyCtrl::CreateEx](#createex)|Crée un contrôle de touche d’accès rapide avec les styles étendus Windows spécifiés et l’attache à un `CHotKeyCtrl` objet.|
|[CHotKeyCtrl::GetHotKey](#gethotkey)|Récupère les indicateurs clés virtuels code et le modificateur de touche d’accès rapide à partir d’un contrôle de touche d’accès rapide.|
|[CHotKeyCtrl::GetHotKeyName](#gethotkeyname)|Récupère le nom de clé dans le jeu de caractères local affecté à une touche d’accès rapide.|
|[CHotKeyCtrl::GetKeyName](#getkeyname)|Récupère le nom de clé dans le jeu de caractères local affecté pour le code de touche virtuelle spécifié.|
|[CHotKeyCtrl::SetHotKey](#sethotkey)|Définit la combinaison de touches à chaud pour un contrôle de touche d’accès rapide.|
|[CHotKeyCtrl::SetRules](#setrules)|Définit les combinaisons non valides et la combinaison du modificateur par défaut pour un contrôle de touche d’accès rapide.|

## <a name="remarks"></a>Notes

Un « contrôle de touche à chaud » est une fenêtre qui permet à l’utilisateur créer une touche d’accès rapide. Une « touche d’accès rapide » est une combinaison de touches que l’utilisateur peut appuyer sur pour effectuer une action rapidement. (Par exemple, un utilisateur peut créer une touche d’accès rapide qui active une fenêtre donnée et le rend au début de l’ordre de plan.) Le contrôle de touche d’accès rapide affiche les choix de l’utilisateur et s’assure que l’utilisateur sélectionne une combinaison de touches valide.

Ce contrôle (et par conséquent la `CHotKeyCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT version 3.51 et ultérieures.

Lorsque l’utilisateur a choisi une combinaison de touches, l’application peut récupérer la combinaison de touches spécifiée à partir du contrôle et le message de message WM_SETHOTKEY permet de configurer la touche d’accès rapide dans le système. Chaque fois que l’utilisateur appuie sur la touche d’accès rapide par la suite, à partir de n’importe quelle partie du système, la fenêtre spécifiée dans le message de message WM_SETHOTKEY reçoit un message WM_SYSCOMMAND spécifiant SC_HOTKEY. Ce message Active la fenêtre qui le reçoit. La touche d’accès rapide reste valide jusqu'à ce que l’application qui a appelé message WM_SETHOTKEY quitte.

Ce mécanisme est différent de la prise en charge clé chaud varie selon le message WM_HOTKEY et le Windows [RegisterHotKey](/windows/desktop/api/winuser/nf-winuser-registerhotkey) et [UnregisterHotKey](/windows/desktop/api/winuser/nf-winuser-unregisterhotkey) fonctions.

Pour plus d’informations sur l’utilisation de `CHotKeyCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="chotkeyctrl"></a>  CHotKeyCtrl::CHotKeyCtrl

Construit un objet `CHotKeyCtrl`.

```
CHotKeyCtrl();
```

##  <a name="create"></a>  CHotKeyCtrl::Create

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
Spécifie le style du contrôle de clé à chaud. Appliquer n’importe quelle combinaison de styles de contrôle. Consultez [des Styles de contrôle courants](/windows/desktop/Controls/common-control-styles) dans le SDK Windows pour plus d’informations.

*rect*<br/>
Spécifie la taille et la position du contrôle de clé à chaud. Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [structure RECT](/windows/desktop/api/windef/ns-windef-tagrect).

*pParentWnd*<br/>
Spécifie la chaud clé fenêtre du contrôle parent, généralement un [CDialog](../../mfc/reference/cdialog-class.md). Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID. du contrôle de clé à chaud

### <a name="return-value"></a>Valeur de retour

Différent de zéro, si l’initialisation a abouti ; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CHotKeyCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, puis `Create`, ce qui crée le contrôle de touche d’accès rapide et l’attache à la `CHotKeyCtrl` objet.

Si vous souhaitez utiliser des styles étendus windows avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create`.

##  <a name="createex"></a>  CHotKeyCtrl::CreateEx

Appelez cette fonction pour créer un contrôle (une fenêtre enfant) et associez-la à la `CHotKeyCtrl` objet.

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
Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle de clé à chaud. Appliquer n’importe quelle combinaison de styles de contrôle. Pour plus d’informations, consultez [des Styles de contrôle courants](/windows/desktop/Controls/common-control-styles) dans le SDK Windows.

*rect*<br/>
Une référence à un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, dans les coordonnées clientes de *pParentWnd*.

*pParentWnd*<br/>
Pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
ID de fenêtre enfant. du contrôle

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.

##  <a name="gethotkey"></a>  CHotKeyCtrl::GetHotKey

Récupère les indicateurs clés virtuels code et le modificateur d’un raccourci clavier à partir d’un contrôle de touche d’accès rapide.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Paramètres

*wVirtualKeyCode*<br/>
[out] Code de touche virtuelle du raccourci clavier. Pour obtenir la liste de codes de touches virtuelles, consultez Winuser.h.

*wModifiers*<br/>
[out] Une combinaison (OR) au niveau du bit des indicateurs qui indiquent les touches de modification dans le raccourci clavier.

Les indicateurs de modificateur sont les suivantes :

|Indicateur|Clé correspondante|
|----------|-----------------------|
|HOTKEYF_ALT|touche ALT|
|HOTKEYF_CONTROL|Touche CTRL enfoncée|
|HOTKEYF_EXT|Clé étendue|
|HOTKEYF_SHIFT|Touche MAJ enfoncée|

### <a name="return-value"></a>Valeur de retour

Dans la première méthode surchargée, une valeur DWORD qui contient les indicateurs de code et le modificateur clés virtuels. L’octet de poids faible du mot de poids faible contient le code de touche virtuelle, l’octet de poids fort du mot de poids faible contient les indicateurs de modificateur et le mot de poids fort est égal à zéro.

### <a name="remarks"></a>Notes

Le code de touche virtuelle et les touches de modification ensemble définissent le raccourci clavier.

##  <a name="gethotkeyname"></a>  CHotKeyCtrl::GetHotKeyName

Appelez cette fonction membre pour obtenir le nom localisé de la touche d’accès rapide.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Valeur de retour

Le nom localisé de la touche d’accès rapide actuellement sélectionné. S’il n’existe aucune touche d’accès rapide sélectionné, `GetHotKeyName` retourne une chaîne vide.

### <a name="remarks"></a>Notes

Le nom retourné par cette fonction membre est fourni à partir du pilote de clavier. Vous pouvez installer un pilote non localisé de clavier dans une version localisée de Windows et vice versa.

##  <a name="getkeyname"></a>  CHotKeyCtrl::GetKeyName

Appelez cette fonction membre pour obtenir le nom localisé de la clé attribué à un code de touche virtuelle spécifié.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Paramètres

*vk*<br/>
Le code de touche virtuelle.

*fExtended*<br/>
Si le code de touche virtuelle est une clé étendue, la valeur TRUE ; Sinon, FALSE.

### <a name="return-value"></a>Valeur de retour

Le nom localisé de la clé spécifiée par le *vk* paramètre. Si la clé n’a aucun nom mappé, `GetKeyName` retourne une chaîne vide.

### <a name="remarks"></a>Notes

Le nom de la clé retournée par cette fonction est fourni à partir du pilote de clavier, donc vous pouvez installer un pilote non localisé de clavier dans une version localisée de Windows et vice versa.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

##  <a name="sethotkey"></a>  CHotKeyCtrl::SetHotKey

Définit le raccourci clavier pour un contrôle de touche d’accès rapide.

```
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Paramètres

*wVirtualKeyCode*<br/>
[in] Code de touche virtuelle du raccourci clavier. Pour obtenir la liste de codes de touches virtuelles, consultez Winuser.h.

*wModifiers*<br/>
[in] Une combinaison (OR) au niveau du bit des indicateurs qui indiquent les touches de modification dans le raccourci clavier.

Les indicateurs de modificateur sont les suivantes :

|Indicateur|Clé correspondante|
|----------|-----------------------|
|HOTKEYF_ALT|touche ALT|
|HOTKEYF_CONTROL|Touche CTRL enfoncée|
|HOTKEYF_EXT|Clé étendue|
|HOTKEYF_SHIFT|Touche MAJ enfoncée|

### <a name="remarks"></a>Notes

Le code de touche virtuelle et les touches de modification ensemble définissent le raccourci clavier.

##  <a name="setrules"></a>  CHotKeyCtrl::SetRules

Appelez cette fonction pour définir les combinaisons non valides et la combinaison du modificateur par défaut pour un contrôle de touche d’accès rapide.

```
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Paramètres

*wInvalidComb*<br/>
Tableau d’indicateurs qui spécifie des combinaisons de touches non valides. Il peut être une combinaison des valeurs suivantes :

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- Clés HKCOMB_NONE non modifié

- HKCOMB_S MAJ

- HKCOMB_SA MAJ + ALT

- HKCOMB_SC MAJ + CTRL

- HKCOMB_SCA MAJ + CTRL + ALT

*wModifiers*<br/>
Tableau d’indicateurs qui spécifie la combinaison de touches à utiliser lors de l’utilisateur entre une combinaison non valide. Pour plus d’informations sur les indicateurs de modificateur, consultez [GetHotKey](#gethotkey).

### <a name="remarks"></a>Notes

Lorsqu’un utilisateur entre une combinaison de clé non valide, tel que défini par les indicateurs spécifiés dans *wInvalidComb*, le système utilise l’opérateur OR pour combiner les touches entrées par l’utilisateur avec les indicateurs spécifiés dans *wModifiers*. La combinaison de touches qui en résulte est convertie en une chaîne, puis affichée dans le contrôle de touche d’accès rapide.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)


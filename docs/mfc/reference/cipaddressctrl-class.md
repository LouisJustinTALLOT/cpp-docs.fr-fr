---
title: CIPAddressCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: 28aa0e7137647bc49406dab1e82b9c2b05ca3538
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372338"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl, classe

Fournit les fonctionnalités du contrôle commun d'adresse IP Windows.

## <a name="syntax"></a>Syntaxe

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Construit un objet `CIPAddressCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Efface le contenu du contrôle des adresses IP.|
|[CIPAddressCtrl::Créer](#create)|Crée un contrôle d’adresse IP `CIPAddressCtrl` et l’attache à un objet.|
|[CIPAddressCtrl::CreateEx](#createex)|Crée un contrôle d’adresse IP avec les styles `CIPAddressCtrl` Windows étendus spécifiés et l’attache à un objet.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Récupère les valeurs d’adresse pour les quatre champs du contrôle des adresses IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Détermine si tous les champs du contrôle des adresses IP sont vides.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Définit les valeurs d’adresse pour les quatre domaines du contrôle des adresses IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Définit la mise au point du clavier sur le champ spécifié dans le contrôle d’adresse IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Définit la plage dans le champ spécifié dans le contrôle d’adresse IP.|

## <a name="remarks"></a>Notes

Un contrôle d’adresse IP, un contrôle similaire à un contrôle de modification, vous permet d’entrer et de manipuler une adresse numérique dans le format Protocole Internet (IP).

Ce contrôle (et `CIPAddressCtrl` donc la classe) n’est disponible que pour les programmes en cours d’exécution sous Microsoft Internet Explorer 4.0 et plus tard. Ils seront également disponibles sous les futures versions de Windows et Windows NT.

Pour plus d’informations générales sur le contrôle des adresses IP, voir [contrôles d’adresse IP](/windows/win32/Controls/ip-address-controls) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

Crée un objet `CIPAddressCtrl` .

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIPAddressCtrl::ClearAddress

Efface le contenu du contrôle des adresses IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress), tel que décrit dans le SDK Windows.

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIPAddressCtrl::Créer

Crée un contrôle d’adresse IP `CIPAddressCtrl` et l’attache à un objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle (en)*<br/>
Le style du contrôle de l’adresse IP. Appliquer une combinaison de styles de fenêtre. Vous devez inclure le style WS_CHILD parce que le contrôle doit être une fenêtre enfant. Voir [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le Windows SDK pour une liste de styles Windows.

*Rect*<br/>
Une référence à la taille et à la position du contrôle d’adresse IP. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Un pointeur à la fenêtre parente du contrôle d’adresse IP. Ce ne doit pas être NULL.

*nID*<br/>
L’ID du contrôle d’adresse IP.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’initialisation a été couronnée de succès; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CIPAddressCtrl` objet en deux étapes.

1. Appelez le constructeur, qui `CIPAddressCtrl` crée l’objet.

1. Appelez `Create`, qui crée le contrôle d’adresse IP.

Si vous souhaitez utiliser des styles windows étendus `Create`avec votre contrôle, appelez [CreateEx](#createex) au lieu de .

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIPAddressCtrl::CreateEx

Appelez cette fonction pour créer un contrôle (une `CIPAddressCtrl` fenêtre enfant) et l’associer à l’objet.

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
Le style du contrôle de l’adresse IP. Appliquer une combinaison de styles de fenêtre. Vous devez inclure le style WS_CHILD parce que le contrôle doit être une fenêtre enfant. Voir [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le Windows SDK pour une liste de styles Windows.

*Rect*<br/>
Une référence à une structure [RECT](/previous-versions/dd162897\(v=vs.85\)) décrivant la taille et la position de la fenêtre à créer, dans les coordonnées des clients de *pParentWnd*.

*pParentWnd*<br/>
Un pointeur vers la fenêtre qui est le parent du contrôle.

*nID*<br/>
L’id de fenêtre pour enfants du contrôle.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles Windows étendus, spécifiés par la préface de style étendu Windows **WS_EX_**.

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIPAddressCtrl::GetAddress

Récupère les valeurs d’adresse pour les quatre champs du contrôle des adresses IP.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Paramètres

*nField0 (en)*<br/>
Une référence à la valeur 0 du champ à partir d’une adresse IP emballée.

*nField1 (en)*<br/>
Une référence à la valeur du champ 1 à partir d’une adresse IP emballée.

*nField2 (en)*<br/>
Une référence à la valeur du champ 2 à partir d’une adresse IP emballée.

*nField3 (en)*<br/>
Une référence à la valeur du champ 3 à partir d’une adresse IP emballée.

*dwAddress (en)*<br/>
Une référence à l’adresse d’une valeur DWORD qui reçoit l’adresse IP. Voir **Remarques** pour une table qui montre comment *dwAddress* est rempli.

### <a name="return-value"></a>Valeur de retour

Nombre de champs non vierges dans le contrôle des adresses IP.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress), tel que décrit dans le SDK Windows. Dans le premier prototype ci-dessus, les nombres dans les champs 0 à 3 du contrôle, lus de gauche à droite respectivement, peuplent les quatre paramètres. Dans le deuxième prototype ci-dessus, *dwAddress* est peuplé comme suit.

|Champ|Bits contenant la valeur du champ|
|-----------|-------------------------------------|
|0|24 à 31 ans|
|1|16 à 23 ans|
|2|8 à 15 ans|
|3|0 à 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIPAddressCtrl::IsBlank

Détermine si tous les champs du contrôle des adresses IP sont vides.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si tous les champs de contrôle des adresses IP sont vides; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank), tel que décrit dans le SDK Windows.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIPAddressCtrl::SetAddress

Définit les valeurs d’adresse pour les quatre domaines du contrôle des adresses IP.

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Paramètres

*nField0 (en)*<br/>
La valeur du champ 0 à partir d’une adresse IP emballée.

*nField1 (en)*<br/>
La valeur du champ 1 à partir d’une adresse IP emballée.

*nField2 (en)*<br/>
La valeur du champ 2 à partir d’une adresse IP emballée.

*nField3 (en)*<br/>
La valeur du champ 3 à partir d’une adresse IP emballée.

*dwAddress (en)*<br/>
Une valeur DWORD qui contient la nouvelle adresse IP. Voir **Remarques** pour une table qui montre comment la valeur DWORD est remplie.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress), tel que décrit dans le SDK Windows. Dans le premier prototype ci-dessus, les nombres dans les champs 0 à 3 du contrôle, lus de gauche à droite respectivement, peuplent les quatre paramètres. Dans le deuxième prototype ci-dessus, *dwAddress* est peuplé comme suit.

|Champ|Bits contenant la valeur du champ|
|-----------|-------------------------------------|
|0|24 à 31 ans|
|1|16 à 23 ans|
|2|8 à 15 ans|
|3|0 à 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

Définit la mise au point du clavier sur le champ spécifié dans le contrôle d’adresse IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Paramètres

*nField (en)*<br/>
Indice de champ à base de zéro auquel l’accent devrait être mis. Si cette valeur est supérieure au nombre de champs, l’accent est mis sur le premier champ blanc. Si tous les champs ne sont pas vides, la mise au point est définie sur le premier champ.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus), tel que décrit dans le SDK Windows.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Définit la plage dans le champ spécifié dans le contrôle d’adresse IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Paramètres

*nField (en)*<br/>
Indice de champ à base zéro auquel la gamme sera appliquée.

*nLower (en)*<br/>
Une référence à un intégrant recevant la limite inférieure du champ spécifié dans ce contrôle d’adresse IP.

*nUpper (en)*<br/>
Une référence à un intégrant recevant la limite supérieure du champ spécifié dans ce contrôle d’adresse IP.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange), tel que décrit dans le SDK Windows. Utilisez les deux paramètres, *nLower* et *nUpper*, pour indiquer les limites inférieures et supérieures du champ, au lieu du *paramètre wRange* utilisé avec le message Win32.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

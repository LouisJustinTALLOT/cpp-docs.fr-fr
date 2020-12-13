---
description: 'En savoir plus sur : classe CIPAddressCtrl'
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
ms.openlocfilehash: e5791726bc31e9b7485d0de7ecfc5461408ed02a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340942"
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
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Efface le contenu du contrôle d’adresse IP.|
|[CIPAddressCtrl :: Create](#create)|Crée un contrôle d’adresse IP et l’attache à un `CIPAddressCtrl` objet.|
|[CIPAddressCtrl :: CreateEx](#createex)|Crée un contrôle d’adresse IP avec les styles étendus Windows spécifiés et l’attache à un `CIPAddressCtrl` objet.|
|[CIPAddressCtrl :: GetAddress](#getaddress)|Récupère les valeurs d’adresse pour les quatre champs dans le contrôle d’adresse IP.|
|[CIPAddressCtrl :: IsBlank](#isblank)|Détermine si tous les champs du contrôle d’adresse IP sont vides.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Définit les valeurs d’adresse pour les quatre champs dans le contrôle d’adresse IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Définit le focus clavier sur le champ spécifié dans le contrôle d’adresse IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Définit la plage dans le champ spécifié dans le contrôle d’adresse IP.|

## <a name="remarks"></a>Notes

Un contrôle d’adresse IP, un contrôle similaire à un contrôle d’édition, vous permet d’entrer et de manipuler une adresse numérique au format IP (Internet Protocol).

Ce contrôle (et par conséquent la `CIPAddressCtrl` classe) est uniquement disponible pour les programmes qui s’exécutent sous Microsoft Internet Explorer 4,0 et versions ultérieures. Ils seront également disponibles dans les prochaines versions de Windows et Windows NT.

Pour plus d’informations générales sur le contrôle d’adresse IP, consultez [contrôles d’adresse IP](/windows/win32/Controls/ip-address-controls) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a> CIPAddressCtrl::CIPAddressCtrl

Crée un objet `CIPAddressCtrl`.

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a> CIPAddressCtrl::ClearAddress

Efface le contenu du contrôle d’adresse IP.

```cpp
void ClearAddress();
```

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress)de message Win32, comme décrit dans le SDK Windows.

## <a name="cipaddressctrlcreate"></a><a name="create"></a> CIPAddressCtrl :: Create

Crée un contrôle d’adresse IP et l’attache à un `CIPAddressCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*<br/>
Style du contrôle d’adresse IP. Appliquez une combinaison de styles de fenêtre. Vous devez inclure le style WS_CHILD, car le contrôle doit être une fenêtre enfant. Consultez [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows pour obtenir la liste des styles Windows.

*rectangulaire*<br/>
Référence à la taille et à la position du contrôle d’adresse IP. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Pointeur vers la fenêtre parente du contrôle d’adresse IP. Il ne doit pas être NULL.

*nID*<br/>
ID du contrôle d’adresse IP.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si l’initialisation a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

Vous construisez un `CIPAddressCtrl` objet en deux étapes.

1. Appelez le constructeur, qui crée l' `CIPAddressCtrl` objet.

1. Appelez `Create` , qui crée le contrôle d’adresse IP.

Si vous souhaitez utiliser des styles Windows étendus avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create` .

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a> CIPAddressCtrl :: CreateEx

Appelez cette fonction pour créer un contrôle (une fenêtre enfant) et l’associer à l' `CIPAddressCtrl` objet.

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
Style du contrôle d’adresse IP. Appliquez une combinaison de styles de fenêtre. Vous devez inclure le style WS_CHILD, car le contrôle doit être une fenêtre enfant. Consultez [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) dans le SDK Windows pour obtenir la liste des styles Windows.

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

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a> CIPAddressCtrl :: GetAddress

Récupère les valeurs d’adresse pour les quatre champs dans le contrôle d’adresse IP.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Paramètres

*nField0*<br/>
Référence à la valeur du champ 0 à partir d’une adresse IP compressée.

*nField1*<br/>
Référence à la valeur champ 1 à partir d’une adresse IP compressée.

*nField2*<br/>
Référence à la valeur du champ 2 à partir d’une adresse IP compressée.

*nField3*<br/>
Référence à la valeur du champ 3 à partir d’une adresse IP compressée.

*dwAddress*<br/>
Référence à l’adresse d’une valeur DWORD qui reçoit l’adresse IP. Consultez la **section Notes** pour obtenir une table qui indique comment *dwAddress* est rempli.

### <a name="return-value"></a>Valeur renvoyée

Nombre de champs non vides dans le contrôle d’adresse IP.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress)de message Win32, comme décrit dans le SDK Windows. Dans le premier prototype ci-dessus, les nombres dans les champs 0 à 3 du contrôle, lire respectivement de gauche à droite, et remplir les quatre paramètres. Dans le deuxième prototype ci-dessus, *dwAddress* est rempli comme suit.

|Champ|Bits contenant la valeur du champ|
|-----------|-------------------------------------|
|0|24 à 31|
|1|16 à 23|
|2|de 8 à 15|
|3|de 0 à 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a> CIPAddressCtrl :: IsBlank

Détermine si tous les champs du contrôle d’adresse IP sont vides.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si tous les champs de contrôle d’adresse IP sont vides ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank)de message Win32, comme décrit dans le SDK Windows.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a> CIPAddressCtrl::SetAddress

Définit les valeurs d’adresse pour les quatre champs dans le contrôle d’adresse IP.

```cpp
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Paramètres

*nField0*<br/>
Valeur du champ 0 d’une adresse IP compressée.

*nField1*<br/>
Valeur du champ 1 à partir d’une adresse IP compressée.

*nField2*<br/>
Valeur du champ 2 d’une adresse IP compressée.

*nField3*<br/>
Valeur du champ 3 à partir d’une adresse IP compressée.

*dwAddress*<br/>
Valeur DWORD qui contient la nouvelle adresse IP. Consultez la **section Notes** pour une table qui indique comment la valeur DWORD est remplie.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)de message Win32, comme décrit dans le SDK Windows. Dans le premier prototype ci-dessus, les nombres dans les champs 0 à 3 du contrôle, lire respectivement de gauche à droite, et remplir les quatre paramètres. Dans le deuxième prototype ci-dessus, *dwAddress* est rempli comme suit.

|Champ|Bits contenant la valeur du champ|
|-----------|-------------------------------------|
|0|24 à 31|
|1|16 à 23|
|2|de 8 à 15|
|3|de 0 à 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a> CIPAddressCtrl::SetFieldFocus

Définit le focus clavier sur le champ spécifié dans le contrôle d’adresse IP.

```cpp
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Paramètres

*nField*<br/>
Index de champ de base zéro auquel le focus doit être défini. Si cette valeur est supérieure au nombre de champs, le focus est défini sur le premier champ vide. Si tous les champs ne sont pas vides, le focus est défini sur le premier champ.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus)de message Win32, comme décrit dans le SDK Windows.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a> CIPAddressCtrl::SetFieldRange

Définit la plage dans le champ spécifié dans le contrôle d’adresse IP.

```cpp
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Paramètres

*nField*<br/>
Index de champ de base zéro auquel la plage sera appliquée.

*nLower*<br/>
Référence à un entier qui reçoit la limite inférieure du champ spécifié dans ce contrôle d’adresse IP.

*nUpper*<br/>
Référence à un entier qui reçoit la limite supérieure du champ spécifié dans ce contrôle d’adresse IP.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange)de message Win32, comme décrit dans le SDK Windows. Utilisez les deux paramètres, *nLower* et *nUpper*, pour indiquer les limites inférieure et supérieure du champ, au lieu du paramètre *WRange* utilisé avec le message Win32.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

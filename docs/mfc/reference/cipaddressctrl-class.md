---
title: Cipaddressctrl, classe
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
ms.openlocfilehash: e569829c100a581e24b5ce05df2f90ac7088024b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266290"
---
# <a name="cipaddressctrl-class"></a>Cipaddressctrl, classe

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
|[CIPAddressCtrl::Create](#create)|Crée un contrôle d’adresse IP et l’attache à un `CIPAddressCtrl` objet.|
|[CIPAddressCtrl::CreateEx](#createex)|Crée un contrôle d’adresse IP avec les styles étendus Windows spécifiés et l’attache à un `CIPAddressCtrl` objet.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Récupère les valeurs d’adresse pour toutes les quatre champs dans le contrôle d’adresse IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Détermine si tous les champs dans le contrôle d’adresse IP sont vides.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Définit les valeurs d’adresse pour toutes les quatre champs dans le contrôle d’adresse IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Définit le focus clavier dans le champ spécifié dans le contrôle d’adresse IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Définit la plage dans le champ spécifié dans le contrôle d’adresse IP.|

## <a name="remarks"></a>Notes

Un contrôle d’adresse IP, un contrôle similaire à un contrôle d’édition, permet d’entrer et de manipuler une adresse numérique au format IP (Internet Protocol).

Ce contrôle (et par conséquent la `CIPAddressCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Microsoft Internet Explorer 4.0 et versions ultérieures. Ils peuvent également être utilisés dans les versions futures de Windows et Windows NT.

Pour obtenir des informations plus générales sur le contrôle d’adresse IP, consultez [contrôles d’adresse IP](/windows/desktop/Controls/ip-address-controls) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl

Crée un objet `CIPAddressCtrl`.

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

Efface le contenu du contrôle d’adresse IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [IPM_CLEARADDRESS](/windows/desktop/Controls/ipm-clearaddress), comme décrit dans le SDK Windows.

##  <a name="create"></a>  CIPAddressCtrl::Create

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
Adresse IP style du contrôle. Appliquer une combinaison de styles de fenêtre. Vous devez inclure le style WS_CHILD, car le contrôle doit être une fenêtre enfant. Consultez [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) dans le SDK Windows pour obtenir la liste des styles de windows.

*rect*<br/>
Une référence à la taille et la position du contrôle d’adresse IP. Il peut s’agir un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure.

*pParentWnd*<br/>
Pointeur vers la fenêtre du parent du contrôle d’adresse IP. Il ne doit pas être NULL.

*nID*<br/>
ID. du contrôle d’adresse IP

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’initialisation a abouti ; sinon 0.

### <a name="remarks"></a>Notes

Vous construisez un `CIPAddressCtrl` objet en deux étapes.

1. Appelez le constructeur, ce qui crée le `CIPAddressCtrl` objet.

1. Appelez `Create`, ce qui crée le contrôle d’adresse IP.

Si vous souhaitez utiliser des styles étendus windows avec votre contrôle, appelez [CreateEx](#createex) au lieu de `Create`.

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

Appelez cette fonction pour créer un contrôle (une fenêtre enfant) et associez-la à la `CIPAddressCtrl` objet.

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
Adresse IP style du contrôle. Appliquer une combinaison de styles de fenêtre. Vous devez inclure le style WS_CHILD, car le contrôle doit être une fenêtre enfant. Consultez [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) dans le SDK Windows pour obtenir la liste des styles de windows.

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

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

Récupère les valeurs d’adresse pour toutes les quatre champs dans le contrôle d’adresse IP.

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
Une référence à la valeur du champ 0 à partir d’une adresse IP compressée.

*nField1*<br/>
Une référence à la valeur du champ de 1 à partir d’une adresse IP compressée.

*nField2*<br/>
Une référence à la valeur du champ 2 à partir d’une adresse IP compressée.

*nField3*<br/>
Une référence à la valeur du champ 3 à partir d’une adresse IP compressée.

*dwAddress*<br/>
Une référence à l’adresse d’une valeur DWORD qui reçoit l’adresse IP. Consultez **remarques** pour une table qui montre comment *dwAddress* est remplie.

### <a name="return-value"></a>Valeur de retour

Le nombre de champs non vides dans le contrôle d’adresse IP.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress), comme décrit dans le SDK Windows. Dans le premier prototype ci-dessus, les numéros dans les champs de 0 à 3 du contrôle, de lecture de gauche à droite respectivement, remplir les quatre paramètres. Dans le prototype de deuxième ci-dessus, *dwAddress* est rempli comme suit.

|Champ|Contenant la valeur du champ de bits|
|-----------|-------------------------------------|
|0|24 à 31|
|1|16 à 23|
|2|8 à 15|
|3|0 à 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

Détermine si tous les champs dans le contrôle d’adresse IP sont vides.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si tous les champs de contrôle de l’adresse IP sont vides ; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [IPM_ISBLANK](/windows/desktop/Controls/ipm-isblank), comme décrit dans le SDK Windows.

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

Définit les valeurs d’adresse pour toutes les quatre champs dans le contrôle d’adresse IP.

```
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Paramètres

*nField0*<br/>
La valeur du champ 0 à partir d’une adresse IP compressée.

*nField1*<br/>
La valeur du champ de 1 à partir d’une adresse IP compressée.

*nField2*<br/>
La valeur du champ 2 à partir d’une adresse IP compressée.

*nField3*<br/>
La valeur du champ 3 à partir d’une adresse IP compressée.

*dwAddress*<br/>
Une valeur DWORD qui contient la nouvelle adresse IP. Consultez **remarques** pour un tableau qui indique la façon dont la valeur DWORD est remplie.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress), comme décrit dans le SDK Windows. Dans le premier prototype ci-dessus, les numéros dans les champs de 0 à 3 du contrôle, de lecture de gauche à droite respectivement, remplir les quatre paramètres. Dans le prototype de deuxième ci-dessus, *dwAddress* est rempli comme suit.

|Champ|Contenant la valeur du champ de bits|
|-----------|-------------------------------------|
|0|24 à 31|
|1|16 à 23|
|2|8 à 15|
|3|0 à 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

Définit le focus clavier dans le champ spécifié dans le contrôle d’adresse IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Paramètres

*nField*<br/>
Index du champ de base zéro à laquelle le focus doit être défini. Si cette valeur est supérieure au nombre de champs, le focus est défini sur le premier champ vide. Si tous les champs sont non vide, le focus est défini sur le premier champ.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [IPM_SETFOCUS](/windows/desktop/Controls/ipm-setfocus), comme décrit dans le SDK Windows.

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

Définit la plage dans le champ spécifié dans le contrôle d’adresse IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Paramètres

*nField*<br/>
Index du champ de base zéro auquel la plage s’appliqueront.

*nLower*<br/>
Une référence à un entier de réception de la limite inférieure du champ spécifié dans ce contrôle d’adresse IP.

*nUpper*<br/>
Une référence à un entier de réception de la limite supérieure du champ spécifié dans ce contrôle d’adresse IP.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement du message Win32 [IPM_SETRANGE](/windows/desktop/Controls/ipm-setrange), comme décrit dans le SDK Windows. Utilisez les deux paramètres, *nLower* et *nUpper*, pour indiquer les limites inférieures et supérieures du champ, au lieu du *wRange* paramètre utilisé avec le message Win32.

## <a name="see-also"></a>Voir aussi

[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)

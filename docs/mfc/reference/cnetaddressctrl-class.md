---
title: Classe CNetAddressCtrl
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 30fc510272afc90ae37b583e807d10c3374df052
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562127"
---
# <a name="cnetaddressctrl-class"></a>Classe CNetAddressCtrl

La classe `CNetAddressCtrl` représente le contrôle d'adresse réseau, que vous pouvez utiliser pour entrer et valider le format des adresses IPv4, IPv6 et DNS nommées.

## <a name="syntax"></a>Syntaxe

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CNetAddressCtrl :: CNetAddressCtrl](#cnetaddressctrl)|Construit un objet `CNetAddressCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNetAddressCtrl :: Create](#create)|Crée un contrôle d’adresse réseau avec les styles spécifiés et l’attache à l' `CNetAddressCtrl` objet actuel.|
|[CNetAddressCtrl :: CreateEx](#createex)|Crée un contrôle d’adresse réseau avec les styles étendus spécifiés et l’attache à l' `CNetAddressCtrl` objet actuel.|
|[CNetAddressCtrl ::D isplayErrorTip](#displayerrortip)|Affiche un info-bulle d’erreur lorsque l’utilisateur entre une adresse réseau non prise en charge dans le contrôle d’adresse réseau actuel.|
|[CNetAddressCtrl :: GetAddress](#getaddress)|Récupère une représentation validée et analysée de l’adresse réseau associée au contrôle d’adresse réseau actuel.|
|[CNetAddressCtrl :: GetAllowType](#getallowtype)|Récupère le type d’adresse réseau que le contrôle d’adresse réseau actuel peut prendre en charge.|
|[CNetAddressCtrl :: SetAllowType](#setallowtype)|Définit le type d’adresse réseau que le contrôle d’adresse réseau actuel peut prendre en charge.|

## <a name="remarks"></a>Notes

Le contrôle d’adresse réseau vérifie que le format de l’adresse entrée par l’utilisateur est correct. Le contrôle ne se connecte pas réellement à l’adresse réseau. La méthode [CNetAddressCtrl :: SetAllowType](#setallowtype) spécifie un ou plusieurs types d’adresses que la méthode [CNetAddressCtrl :: GetAddress](#getaddress) peut analyser et vérifier. Une adresse peut se présenter sous la forme d’une adresse IPv4, IPv6 ou nommée pour un serveur, un réseau, un hôte ou une destination de message de diffusion. Si le format de l’adresse est incorrect, vous pouvez utiliser la méthode [CNetAddressCtrl ::D isplayerrortip](#displayerrortip) pour afficher une boîte de message d’info-bulle qui pointe graphiquement vers la zone de texte du contrôle d’adresse réseau et affiche un message d’erreur prédéfini.

La `CNetAddressCtrl` classe est dérivée de la classe [CEdit](../../mfc/reference/cedit-class.md) . Par conséquent, le contrôle d’adresse réseau permet d’accéder à tous les messages de contrôle d’édition Windows.

L’illustration suivante représente une boîte de dialogue qui contient un contrôle d’adresse réseau. La zone de texte (1) pour le contrôle d’adresse réseau contient une adresse réseau non valide. Le message d’info-bulle (2) s’affiche si l’adresse réseau n’est pas valide.

![Dialogue avec contrôle de l'adresse réseau et info-bulle.](../../mfc/reference/media/cnetaddctrl.png "Dialogue avec contrôle de l'adresse réseau et info-bulle.")

## <a name="example"></a>Exemple

L’exemple de code suivant est une partie d’une boîte de dialogue qui valide une adresse réseau. Les gestionnaires d’événements pour trois cases d’option spécifient que l’adresse réseau peut être l’un des trois types d’adresses. L’utilisateur entre une adresse dans la zone de texte du contrôle réseau, puis appuie sur un bouton pour valider l’adresse. Si l’adresse est valide, un message de réussite s’affiche. dans le cas contraire, le message d’erreur info-bulle prédéfini s’affiche.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Exemple

L’exemple de code suivant du fichier d’en-tête de boîte de dialogue définit les variables [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) et [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) requises par la méthode [CNetAddressCtrl :: GetAddress](#getaddress) .

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

Cette classe est prise en charge dans Windows Vista et versions ultérieures.

Des exigences supplémentaires pour cette classe sont décrites dans [exigences de build pour les contrôles communs Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="cnetaddressctrlcnetaddressctrl"></a><a name="cnetaddressctrl"></a> CNetAddressCtrl :: CNetAddressCtrl

Construit un objet `CNetAddressCtrl`.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Notes

Utilisez la méthode [CNetAddressCtrl :: Create](#create) ou [CNetAddressCtrl :: CreateEx](#createex) pour créer un contrôle réseau et l’attacher à l' `CNetAddressCtrl` objet.

## <a name="cnetaddressctrlcreate"></a><a name="create"></a> CNetAddressCtrl :: Create

Crée un contrôle d’adresse réseau avec les styles spécifiés et l’attache à l' `CNetAddressCtrl` objet actuel.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwStyle*\
dans Combinaison d’opérations de bits de styles à appliquer au contrôle. Pour plus d’informations, consultez [modifier des styles](../../mfc/reference/styles-used-by-mfc.md#edit-styles).

*rectangulaire*\
dans Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle.

*pParentWnd*\
dans Pointeur non null vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle.

*nID*\
dans ID du contrôle.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

## <a name="cnetaddressctrlcreateex"></a><a name="createex"></a> CNetAddressCtrl :: CreateEx

Crée un contrôle d’adresse réseau avec les styles étendus spécifiés et l’attache à l' `CNetAddressCtrl` objet actuel.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*dwExStyle*\
dans Combinaison d’opérations de bits de styles étendus à appliquer au contrôle. Pour plus d’informations, consultez le paramètre *dwExStyle* de la fonction [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) .

*dwStyle*\
dans Combinaison d’opérations de bits (ou) de styles à appliquer au contrôle. Pour plus d’informations, consultez [modifier des styles](../../mfc/reference/styles-used-by-mfc.md#edit-styles).

*rectangulaire*\
dans Référence à une structure [Rect](/windows/win32/api/windef/ns-windef-rect) qui contient la position et la taille du contrôle.

*pParentWnd*\
dans Pointeur non null vers un objet [CWnd](../../mfc/reference/cwnd-class.md) qui est la fenêtre parente du contrôle.

*nID*\
dans ID du contrôle.

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode réussit ; Sinon, FALSe.

## <a name="cnetaddressctrldisplayerrortip"></a><a name="displayerrortip"></a> CNetAddressCtrl ::D isplayErrorTip

Affiche un message d’erreur dans l’info-bulle associée au contrôle d’adresse réseau actuel.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Valeur de retour

Valeur `S_OK` si cette méthode réussit ; sinon, code d’erreur.

### <a name="remarks"></a>Notes

Utilisez la méthode [CNetAddressCtrl :: SetAllowType](#setallowtype) pour spécifier les types d’adresses que le contrôle d’adresse réseau actuel peut prendre en charge. Utilisez la méthode [CNetAddressCtrl :: GetAddress](#getaddress) pour valider et analyser l’adresse réseau entrée par l’utilisateur. Utilisez la méthode [CNetAddressCtrl ::D isplayerrortip](#displayerrortip) pour afficher une info-bulle de message d’erreur si la méthode [CNetAddressCtrl :: GetAddress](#getaddress) échoue.

Ce message appelle la macro [NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip) , qui est décrite dans le SDK Windows. Cette macro envoie le `NCM_DISPLAYERRORTIP` message.

## <a name="cnetaddressctrlgetaddress"></a><a name="getaddress"></a> CNetAddressCtrl :: GetAddress

Récupère une représentation validée et analysée de l’adresse réseau associée au contrôle d’adresse réseau actuel.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Paramètres

*pAddress*<br/>
[in, out] Pointeur vers une structure [NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address) .  Définissez le membre *pAddrInfo* de cette structure sur l’adresse d’une structure [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) avant d’appeler la méthode GetAddress.

### <a name="return-value"></a>Valeur de retour

Valeur S_OK si cette méthode réussit ; Sinon, code d’erreur COM. Pour plus d’informations sur les codes d’erreur possibles, consultez la section valeur de retour de la macro [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) .

### <a name="remarks"></a>Notes

Si cette méthode réussit, la structure [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type) contient des informations supplémentaires sur l’adresse réseau.

Utilisez la méthode [CNetAddressCtrl :: SetAllowType](#setallowtype) pour spécifier les types d’adresses que le contrôle d’adresse réseau actuel peut prendre en charge. Utilisez la méthode [CNetAddressCtrl :: GetAddress](#getaddress) pour valider et analyser l’adresse réseau entrée par l’utilisateur. Utilisez la méthode [CNetAddressCtrl ::D isplayerrortip](#displayerrortip) pour afficher une info-bulle de message d’erreur si la méthode [CNetAddressCtrl :: GetAddress](#getaddress) échoue.

Cette méthode appelle la macro [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress) , qui est décrite dans le SDK Windows. Cette macro envoie le message de NCM_GETADDRESS.

## <a name="cnetaddressctrlgetallowtype"></a><a name="getallowtype"></a> CNetAddressCtrl :: GetAllowType

Récupère le type d’adresse réseau que le contrôle d’adresse réseau actuel peut prendre en charge.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Valeur de retour

Combinaison de bits (OR) d’indicateurs qui spécifie les types d’adresses que le contrôle d’adresse réseau peut prendre en charge. Pour plus d’informations, consultez [NET_STRING](/windows/win32/shell/net-string).

### <a name="remarks"></a>Notes

Ce message appelle la macro [NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype) , qui est décrite dans le SDK Windows. Cette macro envoie le message de NCM_GETALLOWTYPE.

## <a name="cnetaddressctrlsetallowtype"></a><a name="setallowtype"></a> CNetAddressCtrl :: SetAllowType

Définit le type d’adresse réseau que le contrôle d’adresse réseau actuel peut prendre en charge.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Paramètres

*dwAddrMask*\
dans Combinaison de bits (OR) d’indicateurs qui spécifie les types d’adresses que le contrôle d’adresse réseau peut prendre en charge. Pour plus d’informations, consultez [NET_STRING](/windows/win32/shell/net-string).

### <a name="return-value"></a>Valeur de retour

S_OK si cette méthode réussit ; Sinon, code d’erreur COM.

### <a name="remarks"></a>Notes

Utilisez la méthode [CNetAddressCtrl :: SetAllowType](#setallowtype) pour spécifier les types d’adresses que le contrôle d’adresse réseau actuel peut prendre en charge. Utilisez la méthode [CNetAddressCtrl :: GetAddress](#getaddress) pour valider et analyser l’adresse réseau entrée par l’utilisateur. Utilisez la méthode [CNetAddressCtrl ::D isplayerrortip](#displayerrortip) pour afficher une info-bulle de message d’erreur si la méthode [CNetAddressCtrl :: GetAddress](#getaddress) échoue.

Ce message appelle la macro [NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype) , qui est décrite dans le SDK Windows. Cette macro envoie le message de NCM_SETALLOWTYPE.

## <a name="see-also"></a>Voir aussi

[CNetAddressCtrl, classe](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)

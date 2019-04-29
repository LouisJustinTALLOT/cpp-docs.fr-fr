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
ms.openlocfilehash: ec4d7aa6f2a1061e632b81a27a0233cf5fdd1c63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373810"
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
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|Construit un objet `CNetAddressCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|Crée un contrôle d’adresse réseau avec des styles spécifiés et l’attache à actuel `CNetAddressCtrl` objet.|
|[CNetAddressCtrl::CreateEx](#createex)|Crée un contrôle d’adresse réseau avec des styles étendus spécifiés et l’attache à actuel `CNetAddressCtrl` objet.|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|Affiche une info-bulle erreur lorsque l’utilisateur entre une adresse de réseau non pris en charge dans le contrôle d’adresse réseau actuelle.|
|[CNetAddressCtrl::GetAddress](#getaddress)|Récupère une représentation analysée et validée de l’adresse de réseau associé au contrôle d’adresse réseau actuelle.|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|Récupère le type d’adresse réseau prenant en charge le contrôle d’adresse réseau actuelle.|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|Définit le type d’adresse réseau prenant en charge le contrôle d’adresse réseau actuelle.|

## <a name="remarks"></a>Notes

Le contrôle d’adresse réseau vérifie que le format de l’adresse de l’utilisateur entre est correct. Le contrôle ne se connecte pas réellement à l’adresse réseau. Le [CNetAddressCtrl::SetAllowType](#setallowtype) méthode spécifie un ou plusieurs types d’adresse qui le [CNetAddressCtrl::GetAddress](#getaddress) méthode peut analyser et vérifier. Une adresse peut être sous la forme d’IPv4, IPv6 ou adresse nommée d’un serveur, réseau, hôte ou destination de message de diffusion. Si le format de l’adresse est incorrect, vous pouvez utiliser la [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) pour afficher une boîte de message d’info-bulle qui pointe vers la zone de texte du contrôle d’adresse réseau et affiche une liste prédéfinie graphiquement (méthode) message d’erreur.

Le `CNetAddressCtrl` classe est dérivée de la [CEdit](../../mfc/reference/cedit-class.md) classe. Par conséquent, le contrôle d’adresse réseau fournit l’accès à tous les messages de contrôle d’édition Windows.

L’illustration suivante représente une boîte de dialogue qui contient un contrôle d’adresse réseau. Le texte boîte (1) pour le contrôle d’adresse réseau contient une adresse réseau non valide. Le message d’info-bulle (2) s’affiche si l’adresse réseau n’est pas valide.

![Boîte de dialogue avec un contrôle d’adresse réseau et l’info-bulle. ](../../mfc/reference/media/cnetaddctrl.png "Boîte de dialogue avec un contrôle d’adresse réseau et l’info-bulle.")

## <a name="example"></a>Exemple

L’exemple de code suivant est une partie d’une boîte de dialogue qui valide une adresse réseau. Les gestionnaires d’événements pour les trois boutons radio spécifient que l’adresse réseau peut être un des trois types d’adresses. L’utilisateur entre une adresse dans la zone de texte du contrôle de réseau, puis appuie sur un bouton pour valider l’adresse. Si l’adresse est valide, un message de réussite s’affiche ; Sinon, le message d’erreur prédéfinies info-bulle s’affiche.

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>Exemple

L’exemple de code suivant à partir du fichier d’en-tête de boîte de dialogue définit les [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) et [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) variables qui sont requis par le [CNetAddressCtrl::GetAddress](#getaddress)(méthode).

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcmn.h

Cette classe est pris en charge dans Windows Vista et versions ultérieures.

Exigences supplémentaires pour cette classe sont décrites dans [Build Configuration requise pour Windows Vista contrôles communs](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

Construit un objet `CNetAddressCtrl`.

```
CNetAddressCtrl();
```

### <a name="remarks"></a>Notes

Utilisez le [CNetAddressCtrl::Create](#create) ou [CNetAddressCtrl::CreateEx](#createex) méthode pour créer un contrôle de réseau et l’attacher à la `CNetAddressCtrl` objet.

##  <a name="create"></a>  CNetAddressCtrl::Create

Crée un contrôle d’adresse réseau avec des styles spécifiés et l’attache à actuel `CNetAddressCtrl` objet.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwStyle*|[in] Une combinaison au niveau du bit de styles à appliquer au contrôle. Pour plus d’informations, consultez [modifier les Styles](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*rect*|[in] Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui contient la position et la taille du contrôle.|
|*pParentWnd*|[in] Un pointeur non null pour un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parent du contrôle.|
|*nID*|[in] L’ID du contrôle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

Crée un contrôle d’adresse réseau avec des styles étendus spécifiés et l’attache à actuel `CNetAddressCtrl` objet.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwExStyle*|[in] Une combinaison (OR) au niveau du bit des styles étendus à appliquer au contrôle. Pour plus d’informations, consultez le *dwExStyle* paramètre de la [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) (fonction).|
|*dwStyle*|[in] Une combinaison (OR) au niveau du bit de styles à appliquer au contrôle. Pour plus d’informations, consultez [modifier les Styles](../../mfc/reference/styles-used-by-mfc.md#edit-styles).|
|*rect*|[in] Une référence à un [RECT](/previous-versions/dd162897\(v=vs.85\)) structure qui contient la position et la taille du contrôle.|
|*pParentWnd*|[in] Un pointeur non null pour un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parent du contrôle.|
|*nID*|[in] L’ID du contrôle.|

### <a name="return-value"></a>Valeur de retour

TRUE si cette méthode a réussi ; Sinon, FALSE.

##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip

Affiche un message d’erreur dans l’info-bulle qui est associé au contrôle d’adresse réseau actuelle.

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>Valeur de retour

La valeur `S_OK` si cette méthode est réussie ; sinon, un code d’erreur.

### <a name="remarks"></a>Notes

Utilisez le [CNetAddressCtrl::SetAllowType](#setallowtype) méthode pour spécifier les types d’adresses prenant en charge le contrôle d’adresse réseau actuelle. Utilisez le [CNetAddressCtrl::GetAddress](#getaddress) méthode pour valider et d’analyser l’adresse réseau que l’utilisateur entre. Utilisez le [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) méthode pour afficher une info-bulle de message erreur si le [CNetAddressCtrl::GetAddress](#getaddress) méthode est infructueuse.

Ce message appelle la [NetAddr_DisplayErrorTip](/windows/desktop/api/shellapi/nf-shellapi-netaddr_displayerrortip) (macro), qui est décrit dans le SDK Windows. Cette macro envoie le `NCM_DISPLAYERRORTIP` message.

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

Récupère une représentation analysée et validée de l’adresse réseau qui est associé au contrôle d’adresse réseau actuelle.

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>Paramètres

*pAddress*<br/>
[in, out] Pointeur vers un [NC_ADDRESS](/windows/desktop/api/shellapi/ns-shellapi-tagnc_address) structure.  Définir le *pAddrInfo* membre de cette structure à l’adresse d’un [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) structure avant d’appeler la méthode GetAddress.

### <a name="return-value"></a>Valeur de retour

La valeur S_OK si cette méthode a réussi ; Sinon, un code d’erreur COM. Pour plus d’informations sur les codes d’erreur possibles, consultez la section de la valeur de retour de la [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) (macro).

### <a name="remarks"></a>Notes

Si cette méthode réussite, le [NET_ADDRESS_INFO](https://msdn.microsoft.com/library/windows/desktop/bb773346) structure contient des informations supplémentaires sur l’adresse réseau.

Utilisez le [CNetAddressCtrl::SetAllowType](#setallowtype) méthode pour spécifier les types d’adresses, le contrôle d’adresse réseau actuelle peut prendre en charge. Utilisez le [CNetAddressCtrl::GetAddress](#getaddress) méthode pour valider et d’analyser l’adresse réseau que l’utilisateur entre. Utilisez le [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) méthode pour afficher une info-bulle de message erreur si le [CNetAddressCtrl::GetAddress](#getaddress) méthode est infructueuse.

Cette méthode appelle la [NetAddr_GetAddress](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getaddress) (macro), qui est décrit dans le SDK Windows. Cette macro envoie le message NCM_GETADDRESS.

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

Récupère le type d’adresse réseau prenant en charge le contrôle d’adresse réseau actuelle.

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>Valeur de retour

Une combinaison (OR) d’indicateurs qui spécifie les types d’adresses que le contrôle d’adresse réseau peut prendre en charge. Pour plus d’informations, consultez [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).

### <a name="remarks"></a>Notes

Ce message appelle la [NetAddr_GetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_getallowtype) (macro), qui est décrit dans le SDK Windows. Cette macro envoie le message NCM_GETALLOWTYPE.

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

Définit le type d’adresse réseau prenant en charge le contrôle d’adresse réseau actuelle.

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwAddrMask*|[in] Une combinaison (OR) d’indicateurs qui spécifie les types d’adresses que le contrôle d’adresse réseau peut prendre en charge. Pour plus d’informations, consultez [NET_STRING](https://msdn.microsoft.com/library/windows/desktop/bb762586).|

### <a name="return-value"></a>Valeur de retour

S_OK si cette méthode a réussi ; Sinon, un code d’erreur COM.

### <a name="remarks"></a>Notes

Utilisez le [CNetAddressCtrl::SetAllowType](#setallowtype) méthode pour spécifier les types d’adresses prenant en charge le contrôle d’adresse réseau actuelle. Utilisez le [CNetAddressCtrl::GetAddress](#getaddress) méthode pour valider et d’analyser l’adresse réseau que l’utilisateur entre. Utilisez le [CNetAddressCtrl::DisplayErrorTip](#displayerrortip) méthode pour afficher une info-bulle de message erreur si le [CNetAddressCtrl::GetAddress](#getaddress) méthode est infructueuse.

Ce message appelle la [NetAddr_SetAllowType](/windows/desktop/api/shellapi/nf-shellapi-netaddr_setallowtype) (macro), qui est décrit dans le SDK Windows. Cette macro envoie le message NCM_SETALLOWTYPE.

## <a name="see-also"></a>Voir aussi

[CNetAddressCtrl, classe](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CEdit, classe](../../mfc/reference/cedit-class.md)

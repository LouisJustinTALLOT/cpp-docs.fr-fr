---
title: Classe COleDispatchDriver
ms.date: 11/04/2016
f1_keywords:
- COleDispatchDriver
- AFXDISP/COleDispatchDriver
- AFXDISP/COleDispatchDriver::COleDispatchDriver
- AFXDISP/COleDispatchDriver::AttachDispatch
- AFXDISP/COleDispatchDriver::CreateDispatch
- AFXDISP/COleDispatchDriver::DetachDispatch
- AFXDISP/COleDispatchDriver::GetProperty
- AFXDISP/COleDispatchDriver::InvokeHelper
- AFXDISP/COleDispatchDriver::ReleaseDispatch
- AFXDISP/COleDispatchDriver::SetProperty
- AFXDISP/COleDispatchDriver::m_bAutoRelease
- AFXDISP/COleDispatchDriver::m_lpDispatch
helpviewer_keywords:
- COleDispatchDriver [MFC], COleDispatchDriver
- COleDispatchDriver [MFC], AttachDispatch
- COleDispatchDriver [MFC], CreateDispatch
- COleDispatchDriver [MFC], DetachDispatch
- COleDispatchDriver [MFC], GetProperty
- COleDispatchDriver [MFC], InvokeHelper
- COleDispatchDriver [MFC], ReleaseDispatch
- COleDispatchDriver [MFC], SetProperty
- COleDispatchDriver [MFC], m_bAutoRelease
- COleDispatchDriver [MFC], m_lpDispatch
ms.assetid: 3ed98daf-cdc7-4374-8a0c-cf695a8d3657
ms.openlocfilehash: 2b52ed3137a9a515278e018d69751aedaddb0cf1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753880"
---
# <a name="coledispatchdriver-class"></a>Classe COleDispatchDriver

Implémente le côté client d'OLE automation.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchDriver
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Construit un objet `COleDispatchDriver`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Attache une `IDispatch` connexion `COleDispatchDriver` à l’objet.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Crée `IDispatch` une connexion et l’attache à l’objet. `COleDispatchDriver`|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Détache une `IDispatch` connexion, sans la relâcher.|
|[COleDispatchDriver::GetProperty](#getproperty)|Obtient une propriété d’automatisation.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Aide pour appeler les méthodes d’automatisation.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Libère `IDispatch` une connexion.|
|[COleDispatchDriver::SetProperty](#setproperty)|Définit une propriété d’automatisation.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::opérateur](#operator_eq)|Copie la valeur `COleDispatchDriver` source dans l’objet.|
|[COleDispatchDriver::opérateur LPDISPATCH](#operator_lpdispatch)|Accéde au `IDispatch` pointeur sous-jacent.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Précise s’il faut `IDispatch` `ReleaseDispatch` libérer la destruction pendante ou de l’objet.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Indique le pointeur à `IDispatch` `COleDispatchDriver`l’interface attachée à ceci .|

## <a name="remarks"></a>Notes

`COleDispatchDriver`n’a pas de classe de base.

Les interfaces de répartition OLE donnent accès aux méthodes et aux propriétés d’un objet. Fonctions membres `COleDispatchDriver` d’attacher, détacher, créer et `IDispatch`libérer une connexion de répartition de type . D’autres fonctions membres utilisent `IDispatch::Invoke`des listes d’arguments variables pour simplifier l’appel .

Cette classe peut être utilisée directement, mais elle n’est généralement utilisée que par des classes créées par l’assistant de classe Add. Lorsque vous créez de nouvelles classes de CMD en important `COleDispatchDriver`une bibliothèque de type, les nouvelles classes sont dérivées de .

Pour plus d’informations sur l’utilisation `COleDispatchDriver`, voir les articles suivants:

- [Clients Automation](../../mfc/automation-clients.md)

- [Serveurs Automation](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleDispatchDriver`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a>COleDispatchDriver::AttachDispatch

Appelez la fonction membre `AttachDispatch` pour attacher un pointeur `IDispatch` vers l’objet `COleDispatchDriver` . Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```cpp
void AttachDispatch(
    LPDISPATCH lpDispatch,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpDispatch*<br/>
Pointeur vers un objet `IDispatch` OLE à attacher à l’objet `COleDispatchDriver` .

*bAutoRelease*<br/>
Spécifie si l’objet dispatch doit être libéré lorsque cet objet est hors de portée.

### <a name="remarks"></a>Notes

Cette fonction libère tout pointeur `IDispatch` qui est déjà attaché à l’objet `COleDispatchDriver` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#3](../../mfc/codesnippet/cpp/coledispatchdriver-class_1.cpp)]

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a>COleDispatchDriver::COleDispatchDriver

Construit un objet `COleDispatchDriver`.

```
COleDispatchDriver();
COleDispatchDriver(LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE);
COleDispatchDriver(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Paramètres

*lpDispatch*<br/>
Pointeur vers un objet `IDispatch` OLE à attacher à l’objet `COleDispatchDriver` .

*bAutoRelease*<br/>
Spécifie si l’objet dispatch doit être libéré lorsque cet objet est hors de portée.

*dispatchSrc*<br/>
Référence à `COleDispatchDriver` un objet existant.

### <a name="remarks"></a>Notes

Le `COleDispatchDriver`formulaire `LPDISPATCH lpDispatch`( , **BOOL**`bAutoRelease` = **TRUE**) connecte l’interface [IDispatch.](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

Le `COleDispatchDriver`formulaire ( **const**`COleDispatchDriver`& `dispatchSrc` `COleDispatchDriver` ) copie un objet existant et incrédilise le nombre de références.

La `COleDispatchDriver`forme ( `COleDispatchDriver` ) crée un `IDispatch` objet mais ne relie pas l’interface. Avant `COleDispatchDriver`d’utiliser ( ) sans `IDispatch` arguments, vous devez connecter un à elle en utilisant soit [COleDispatchDriver::CreateDispatch](#createdispatch) ou [COleDispatchDriver::AttachDispatch](#attachdispatch). Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a>COleDispatchDriver::CreateDispatch

Crée un objet d’interface [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) et l’attache à l’objet `COleDispatchDriver` .

```
BOOL CreateDispatch(
    REFCLSID clsid,
    COleException* pError = NULL);

BOOL CreateDispatch(
    LPCTSTR lpszProgID,
    COleException* pError = NULL);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
ID de classe de l’objet de connexion `IDispatch` à créer.

*Perror*<br/>
Pointeur vers un objet d’exception OLE qui contiendra le code d’état résultant de la création.

*lpszProgID*<br/>
Pointeur vers l’identificateur de programmation, comme « Excel.Document.5 », de l’objet d’automation pour lequel l’objet de répartition doit être créé.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a>COleDispatchDriver::DetachDispatch

Détache la connexion `IDispatch` actuelle de cet objet.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur l’objet OLE `IDispatch` précédemment attaché.

### <a name="remarks"></a>Notes

Le `IDispatch` n’est pas libéré.

Pour plus d’informations sur le type LPDISPATCH, voir [La mise en œuvre de l’interface IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a>COleDispatchDriver::GetProperty

Obtient la propriété de l’objet spécifié par *dwDispID*.

```cpp
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Paramètres

*dwDispID*<br/>
Identifie la propriété à récupérer.

*vtProp (en)*<br/>
Spécifie la propriété à récupérer. Pour connaître les valeurs possibles, consultez la section Notes de [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp (en)*<br/>
Adresse de la variable qui recevra la valeur de la propriété. Il doit correspondre au type spécifié par *vtProp*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a>COleDispatchDriver::InvokeHelper

Appelle la méthode de l’objet ou la propriété spécifiée par *dwDispID*, dans le contexte spécifié par *wFlags*.

```cpp
void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>Paramètres

*dwDispID*<br/>
Identifie la méthode ou propriété à appeler.

*wFlags (en)*<br/>
Drapeaux décrivant le contexte `IDispatch::Invoke`de l’appel à . . Pour une liste de valeurs possibles, voir le *paramètre wFlags* dans [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) in the Windows SDK.

*vtRet (en)*<br/>
Spécifie le type de la valeur de retour. Pour connaître les valeurs possibles, consultez la section Notes.

*pvRet*<br/>
Adresse de la variable qui recevra la valeur de propriété ou la valeur de retour. Il doit correspondre au type spécifié par *vtRet*.

*pbParamInfo*<br/>
Pointeur vers une chaîne d’octets à durée nulle spécifiant les types de paramètres suivant *pbParamInfo*.

*...*<br/>
Liste variable des paramètres, des types spécifiés dans *pbParamInfo*.

### <a name="remarks"></a>Notes

Le *paramètre pbParamInfo* spécifie les types de paramètres transmis à la méthode ou à la propriété. La liste variable d’arguments est représentée par **...** dans la déclaration de syntaxe.

Les valeurs possibles pour l’argument *vtRet* sont tirées de l’énumération VARENUM. Les valeurs possibles sont les suivantes :

|Symbole|Type de retour|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**Court**|
|VT_I4|**Long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**Date**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**Bool**|
|VT_VARIANT|**Variante**|
|VT_UNKNOWN|LPUNKNOWN|

*L’argument pbParamInfo* est une liste séparée de l’espace de **constantes VTS_.** Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste des paramètres de la fonction. Les valeurs possibles sont répertoriées avec la macro [EVENT_CUSTOM](event-maps.md#event_custom) .

Cette fonction convertit les paramètres en valeurs VARIANTARG , puis appelle la méthode [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Si l’appel à `Invoke` échoue, cette fonction lève une exception. Si le SCODE (code `IDispatch::Invoke` d’état) retourné par est DISP_E_EXCEPTION, cette fonction jette un objet [COleException;](../../mfc/reference/coleexception-class.md) sinon il jette un [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Pour plus d’informations, voir [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [Mise en œuvre de l’interface IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke), et [structure des codes d’erreur COM](/windows/win32/com/structure-of-com-error-codes) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a>COleDispatchDriver::m_bAutoRelease

Si VRAI, l’objet COM accessible par [m_lpDispatch](#m_lpdispatch) sera automatiquement libéré lorsque [ReleaseDispatch](#releasedispatch) est appelé ou lorsque cet `COleDispatchDriver` objet est détruit.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Notes

Par défaut, `m_bAutoRelease` est réglé à VRAI dans le constructeur.

Pour plus d’informations sur la libération d’objets COM, voir [Implementing Reference Counting](/windows/win32/com/implementing-reference-counting) et [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) in the Windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a>COleDispatchDriver::m_lpDispatch

Le pointeur `IDispatch` de l’interface attachée à cette `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Notes

Le `m_lpDispatch` membre des données est une variable publique de type LPDISPATCH.

Pour plus d’informations, voir [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) dans le SDK Windows.

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a>COleDispatchDriver::opérateur

Copie la valeur `COleDispatchDriver` source dans l’objet.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Paramètres

*dispatchSrc*<br/>
Un pointeur `COleDispatchDriver` vers un objet existant.

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a>COleDispatchDriver::opérateur LPDISPATCH

Accéde au `IDispatch` pointeur `COleDispatchDriver` sous-jacent de l’objet.

```
operator LPDISPATCH();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a>COleDispatchDriver::ReleaseDispatch

Libère `IDispatch` la connexion. Pour plus d’informations, voir [Mise en œuvre de l’interface IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>Notes

Si la version automatique a été définie `IDispatch::Release` pour cette connexion, cette fonction appelle avant de libérer l’interface.

### <a name="example"></a>Exemple

  Voir l’exemple pour [COleDispatchDriver::AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a>COleDispatchDriver::SetProperty

Définit la propriété de l’objet OLE spécifiée par *dwDispID*.

```cpp
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Paramètres

*dwDispID*<br/>
Identifie la propriété à définir.

*vtProp (en)*<br/>
Spécifie le type de la propriété à définir. Pour connaître les valeurs possibles, consultez la section Notes de [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Un seul paramètre du type spécifié par *vtProp*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Échantillon MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)

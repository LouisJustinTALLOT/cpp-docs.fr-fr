---
description: 'En savoir plus sur : classe COleDispatchDriver'
title: COleDispatchDriver, classe
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
ms.openlocfilehash: 0006f7922820602dd7a4a927b8064fc9e75f76f2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227245"
---
# <a name="coledispatchdriver-class"></a>COleDispatchDriver, classe

Implémente le côté client d'OLE automation.

## <a name="syntax"></a>Syntaxe

```
class COleDispatchDriver
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver :: COleDispatchDriver](#coledispatchdriver)|Construit un objet `COleDispatchDriver`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver :: AttachDispatch](#attachdispatch)|Attache une `IDispatch` connexion à l' `COleDispatchDriver` objet.|
|[COleDispatchDriver :: CreateDispatch](#createdispatch)|Crée une `IDispatch` connexion et l’attache à l' `COleDispatchDriver` objet.|
|[COleDispatchDriver ::D etachDispatch](#detachdispatch)|Détache une `IDispatch` connexion, sans la libérer.|
|[COleDispatchDriver :: GetProperty](#getproperty)|Obtient une propriété Automation.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Assistance pour appeler des méthodes Automation.|
|[COleDispatchDriver :: ReleaseDispatch](#releasedispatch)|Libère une `IDispatch` connexion.|
|[COleDispatchDriver :: SetProperty](#setproperty)|Définit une propriété Automation.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver :: Operator =](#operator_eq)|Copie la valeur source dans l' `COleDispatchDriver` objet.|
|[COleDispatchDriver :: Operator LPDISPATCH](#operator_lpdispatch)|Accède au pointeur sous-jacent `IDispatch` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver :: m_bAutoRelease](#m_bautorelease)|Spécifie s’il faut libérer le `IDispatch` pendant ou la destruction de l' `ReleaseDispatch` objet.|
|[COleDispatchDriver :: m_lpDispatch](#m_lpdispatch)|Indique le pointeur vers l' `IDispatch` interface attachée à ce `COleDispatchDriver` .|

## <a name="remarks"></a>Notes

`COleDispatchDriver` n’a pas de classe de base.

Les interfaces de dispatch OLE fournissent l’accès aux méthodes et propriétés d’un objet. Fonctions membres de l' `COleDispatchDriver` attachement, du détachement, de la création et de la libération d’une connexion de dispatch de type `IDispatch` . D’autres fonctions membres utilisent des listes d’arguments variables pour simplifier l’appel de `IDispatch::Invoke` .

Cette classe peut être utilisée directement, mais elle est généralement utilisée uniquement par les classes créées par l’Assistant Ajout d’une classe. Lorsque vous créez de nouvelles classes C++ en important une bibliothèque de types, les nouvelles classes sont dérivées de `COleDispatchDriver` .

Pour plus d’informations sur l’utilisation de `COleDispatchDriver` , consultez les articles suivants :

- [Clients Automation](../../mfc/automation-clients.md)

- [Serveurs Automation](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleDispatchDriver`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coledispatchdriverattachdispatch"></a><a name="attachdispatch"></a> COleDispatchDriver :: AttachDispatch

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

## <a name="coledispatchdrivercoledispatchdriver"></a><a name="coledispatchdriver"></a> COleDispatchDriver :: COleDispatchDriver

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
Référence à un `COleDispatchDriver` objet existant.

### <a name="remarks"></a>Notes

Le formulaire `COleDispatchDriver( LPDISPATCH lpDispatch, BOOL bAutoRelease = TRUE )` connecte l’interface [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

Le formulaire `COleDispatchDriver( const COleDispatchDriver& dispatchSrc )` copie un `COleDispatchDriver` objet existant et incrémente le décompte de références.

Le formulaire `COleDispatchDriver( )` crée un `COleDispatchDriver` objet, mais ne connecte pas l' `IDispatch` interface. Avant d’utiliser `COleDispatchDriver( )` sans arguments, vous devez en connecter un `IDispatch` à l’aide de [COleDispatchDriver :: CreateDispatch](#createdispatch) ou de [COleDispatchDriver :: AttachDispatch](#attachdispatch). Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdrivercreatedispatch"></a><a name="createdispatch"></a> COleDispatchDriver :: CreateDispatch

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

*identificateur*<br/>
ID de classe de l’objet de connexion `IDispatch` à créer.

*pError*<br/>
Pointeur vers un objet d’exception OLE qui contiendra le code d’état résultant de la création.

*lpszProgID*<br/>
Pointeur vers l’identificateur de programmation, comme « Excel.Document.5 », de l’objet d’automation pour lequel l’objet de répartition doit être créé.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

## <a name="coledispatchdriverdetachdispatch"></a><a name="detachdispatch"></a> COleDispatchDriver ::D etachDispatch

Détache la connexion actuelle `IDispatch` de cet objet.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet OLE précédemment attaché `IDispatch` .

### <a name="remarks"></a>Notes

`IDispatch`N’est pas libéré.

Pour plus d’informations sur le type LPDISPATCH, consultez [implémentation de l’interface IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

## <a name="coledispatchdrivergetproperty"></a><a name="getproperty"></a> COleDispatchDriver :: GetProperty

Obtient la propriété de l’objet spécifiée par *dwDispID*.

```cpp
void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>Paramètres

*dwDispID*<br/>
Identifie la propriété à récupérer.

*vtProp*<br/>
Spécifie la propriété à récupérer. Pour connaître les valeurs possibles, consultez la section Notes de [COleDispatchDriver::InvokeHelper](#invokehelper).

*pvProp*<br/>
Adresse de la variable qui recevra la valeur de la propriété. Il doit correspondre au type spécifié par *vtProp*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

## <a name="coledispatchdriverinvokehelper"></a><a name="invokehelper"></a> COleDispatchDriver :: InvokeHelper

Appelle la méthode ou la propriété de l’objet spécifiée par *dwDispID*, dans le contexte spécifié par *wFlags*.

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

*wFlags*<br/>
Indicateurs décrivant le contexte de l’appel à `IDispatch::Invoke` . . Pour obtenir la liste des valeurs possibles, consultez le paramètre *wFlags* dans [IDispatch :: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) dans le SDK Windows.

*vtRet*<br/>
Spécifie le type de la valeur de retour. Pour connaître les valeurs possibles, consultez la section Notes.

*pvRet*<br/>
Adresse de la variable qui recevra la valeur de propriété ou la valeur de retour. Il doit correspondre au type spécifié par *vtRet*.

*pbParamInfo*<br/>
Pointeur vers une chaîne d’octets se terminant par un caractère null qui spécifie les types des paramètres après *pbParamInfo*.

*...*<br/>
Liste variable de paramètres, des types spécifiés dans *pbParamInfo*.

### <a name="remarks"></a>Notes

Le paramètre *pbParamInfo* spécifie les types des paramètres passés à la méthode ou à la propriété. La liste variable d’arguments est représentée par **...** dans la déclaration de syntaxe.

Les valeurs possibles de l’argument *vtRet* sont extraites de l’énumération VarEnum. Les valeurs possibles sont les suivantes :

|Symbole|Type de retour|
|------------|-----------------|
|VT_EMPTY|**`void`**|
|VT_I2|**`short`**|
|VT_I4|**`long`**|
|VT_R4|**`float`**|
|VT_R8|**`double`**|
|VT_CY|**CY**|
|VT_DATE|**DATE**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**Boolean**|
|VT_VARIANT|**DIFFÉRENT**|
|VT_UNKNOWN|LPUNKNOWN|

L’argument *pbParamInfo* est une liste séparée par des espaces de constantes de **VTS_** . Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste des paramètres de la fonction. Les valeurs possibles sont répertoriées avec la macro [EVENT_CUSTOM](event-maps.md#event_custom) .

Cette fonction convertit les paramètres en valeurs VARIANTARG , puis appelle la méthode [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) . Si l’appel à `Invoke` échoue, cette fonction lève une exception. Si le SCODE (code d’État) retourné par `IDispatch::Invoke` est DISP_E_EXCEPTION, cette fonction lève un objet [COleException](../../mfc/reference/coleexception-class.md) ; sinon, elle lève une [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Pour plus d’informations, consultez [VARIANTARG](/windows/win32/api/oaidl/ns-oaidl-variant), [Implementing the IDispatch interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch :: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)et [Structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) in the SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](#createdispatch).

## <a name="coledispatchdriverm_bautorelease"></a><a name="m_bautorelease"></a> COleDispatchDriver :: m_bAutoRelease

Si la valeur est TRUE, l’objet COM accessible par [m_lpDispatch](#m_lpdispatch) est automatiquement libéré quand [ReleaseDispatch](#releasedispatch) est appelé ou lorsque cet `COleDispatchDriver` objet est détruit.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Notes

Par défaut, `m_bAutoRelease` a la valeur true dans le constructeur.

Pour plus d’informations sur la libération d’objets COM, consultez [implémentation du décompte de références](/windows/win32/com/implementing-reference-counting) et [IUnknown :: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

## <a name="coledispatchdriverm_lpdispatch"></a><a name="m_lpdispatch"></a> COleDispatchDriver :: m_lpDispatch

Pointeur vers l' `IDispatch` interface attachée à ce `COleDispatchDriver` .

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Notes

Le `m_lpDispatch` membre de données est une variable publique de type LPDISPATCH.

Pour plus d’informations, consultez [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver :: AttachDispatch](#attachdispatch).

## <a name="coledispatchdriveroperator-"></a><a name="operator_eq"></a> COleDispatchDriver :: Operator =

Copie la valeur source dans l' `COleDispatchDriver` objet.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Paramètres

*dispatchSrc*<br/>
Pointeur vers un objet existant `COleDispatchDriver` .

## <a name="coledispatchdriveroperator-lpdispatch"></a><a name="operator_lpdispatch"></a> COleDispatchDriver :: Operator LPDISPATCH

Accède au pointeur sous-jacent `IDispatch` de l' `COleDispatchDriver` objet.

```
operator LPDISPATCH();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

## <a name="coledispatchdriverreleasedispatch"></a><a name="releasedispatch"></a> COleDispatchDriver :: ReleaseDispatch

Libère la `IDispatch` connexion. Pour plus d’informations, consultez [implémentation de l’interface IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) .

```cpp
void ReleaseDispatch();
```

### <a name="remarks"></a>Notes

Si la mise en sortie automatique a été définie pour cette connexion, cette fonction appelle `IDispatch::Release` avant de libérer l’interface.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver :: AttachDispatch](#attachdispatch).

## <a name="coledispatchdriversetproperty"></a><a name="setproperty"></a> COleDispatchDriver :: SetProperty

Définit la propriété de l’objet OLE spécifiée par *dwDispID*.

```cpp
void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>Paramètres

*dwDispID*<br/>
Identifie la propriété à définir.

*vtProp*<br/>
Spécifie le type de la propriété à définir. Pour connaître les valeurs possibles, consultez la section Notes de [COleDispatchDriver::InvokeHelper](#invokehelper).

*...*<br/>
Paramètre unique du type spécifié par *vtProp*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC ACDual](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)

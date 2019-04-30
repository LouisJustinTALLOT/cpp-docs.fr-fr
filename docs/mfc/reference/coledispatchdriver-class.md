---
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
ms.openlocfilehash: c0c1fd14105bae3b5413f92b547339ccabf3bb91
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341611"
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
|[COleDispatchDriver::COleDispatchDriver](#coledispatchdriver)|Construit un objet `COleDispatchDriver`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::AttachDispatch](#attachdispatch)|Attache un `IDispatch` connexion à la `COleDispatchDriver` objet.|
|[COleDispatchDriver::CreateDispatch](#createdispatch)|Crée un `IDispatch` connexion et l’attache à la `COleDispatchDriver` objet.|
|[COleDispatchDriver::DetachDispatch](#detachdispatch)|Détache un `IDispatch` connexion, sans le libérer.|
|[COleDispatchDriver::GetProperty](#getproperty)|Obtient une propriété automation.|
|[COleDispatchDriver::InvokeHelper](#invokehelper)|Programme d’assistance pour appeler des méthodes d’automatisation.|
|[COleDispatchDriver::ReleaseDispatch](#releasedispatch)|Versions une `IDispatch` connexion.|
|[COleDispatchDriver::SetProperty](#setproperty)|Définit une propriété automation.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::operator =](#operator_eq)|Copie la valeur de la source dans le `COleDispatchDriver` objet.|
|[COleDispatchDriver::operator LPDISPATCH](#operator_lpdispatch)|Accède à sous-jacent `IDispatch` pointeur.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[COleDispatchDriver::m_bAutoRelease](#m_bautorelease)|Spécifie s’il faut libérer le `IDispatch` pendant `ReleaseDispatch` ou la destruction d’objets.|
|[COleDispatchDriver::m_lpDispatch](#m_lpdispatch)|Indique le pointeur vers le `IDispatch` interface attachée à ce `COleDispatchDriver`.|

## <a name="remarks"></a>Notes

`COleDispatchDriver` n’a pas d’une classe de base.

Interfaces de dispatch OLE fournissent un accès aux méthodes et aux propriétés d’un objet. Fonctions membres de `COleDispatchDriver` attacher, détacher, créer et libérer une connexion de dispatch de type `IDispatch`. Autres fonctions membres utilisent des listes d’arguments variables pour simplifier l’appel `IDispatch::Invoke`.

Cette classe peut être utilisée directement, mais il est généralement utilisé uniquement par les classes créées par l’Assistant Ajouter une classe. Lorsque vous créez de nouvelles classes C++ en important une bibliothèque de types, les nouvelles classes sont dérivées de `COleDispatchDriver`.

Pour plus d’informations sur l’utilisation de `COleDispatchDriver`, consultez les articles suivants :

- [Clients Automation](../../mfc/automation-clients.md)

- [Serveurs Automation](../../mfc/automation-servers.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`COleDispatchDriver`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="attachdispatch"></a>  COleDispatchDriver::AttachDispatch

Appelez la fonction membre `AttachDispatch` pour attacher un pointeur `IDispatch` vers l’objet `COleDispatchDriver` . Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

```
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

##  <a name="coledispatchdriver"></a>  COleDispatchDriver::COleDispatchDriver

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
Référence à un existant `COleDispatchDriver` objet.

### <a name="remarks"></a>Notes

Le formulaire `COleDispatchDriver`( `LPDISPATCH lpDispatch`, **BOOL**`bAutoRelease` = **TRUE**) se connecte le [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) interface.

Le formulaire `COleDispatchDriver`( **const**`COleDispatchDriver`& `dispatchSrc`) copie existante `COleDispatchDriver` de l’objet et incrémente le décompte de références.

Le formulaire `COleDispatchDriver`() crée un `COleDispatchDriver` de l’objet, mais ne se connecte pas le `IDispatch` interface. Avant d’utiliser `COleDispatchDriver`() sans arguments, vous devez vous connecter un `IDispatch` à l’aide soit [COleDispatchDriver::CreateDispatch](#createdispatch) ou [COleDispatchDriver::AttachDispatch](#attachdispatch). Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](#createdispatch).

##  <a name="createdispatch"></a>  COleDispatchDriver::CreateDispatch

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

*pError*<br/>
Pointeur vers un objet d’exception OLE qui contiendra le code d’état résultant de la création.

*lpszProgID*<br/>
Pointeur vers l’identificateur de programmation, comme « Excel.Document.5 », de l’objet d’automation pour lequel l’objet de répartition doit être créé.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#4](../../mfc/codesnippet/cpp/coledispatchdriver-class_2.cpp)]

##  <a name="detachdispatch"></a>  COleDispatchDriver::DetachDispatch

Détache actuel `IDispatch` connexion à partir de cet objet.

```
LPDISPATCH DetachDispatch();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’OLE précédemment attaché `IDispatch` objet.

### <a name="remarks"></a>Notes

Le `IDispatch` n’est pas libérée.

Pour plus d’informations sur le type LPDISPATCH, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#5](../../mfc/codesnippet/cpp/coledispatchdriver-class_3.cpp)]

##  <a name="getproperty"></a>  COleDispatchDriver::GetProperty

Obtient la propriété de l’objet spécifiée par *dwDispID*.

```
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
Adresse de la variable qui recevra la valeur de propriété. Il doit correspondre au type spécifié par *vtProp*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#6](../../mfc/codesnippet/cpp/coledispatchdriver-class_4.cpp)]

##  <a name="invokehelper"></a>  COleDispatchDriver::InvokeHelper

Appelle la méthode de l’objet ou la propriété spécifiée par *dwDispID*, dans le contexte spécifié par *wFlags*.

```
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
Indicateurs décrivant le contexte de l’appel à `IDispatch::Invoke`. . Pour obtenir la liste des valeurs possibles, consultez le *wFlags* paramètre dans [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) dans le SDK Windows.

*vtRet*<br/>
Spécifie le type de la valeur de retour. Pour connaître les valeurs possibles, consultez la section Notes.

*pvRet*<br/>
Adresse de la variable qui recevra la valeur de propriété ou la valeur de retour. Il doit correspondre au type spécifié par *vtRet*.

*pbParamInfo*<br/>
Pointeur vers une chaîne se terminant par null d’octets spécifiant les types de paramètres suivant *pbParamInfo*.

*...*<br/>
Liste de variables de paramètres, des types spécifiés dans *pbParamInfo*.

### <a name="remarks"></a>Notes

Le *pbParamInfo* paramètre spécifie les types des paramètres passés à la méthode ou propriété. La liste variable d’arguments est représentée par **...** dans la déclaration de syntaxe.

Les valeurs possibles pour le *vtRet* argument proviennent de l’énumération VARENUM. Les valeurs possibles sont les suivantes :

|Symbole|Type de retour|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|**CY**|
|VT_DATE|**DATE**|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|**BOOL**|
|VT_VARIANT|**VARIANT**|
|VT_UNKNOWN|LPUNKNOWN|

Le *pbParamInfo* argument est une liste séparée par des espaces de **VTS_** constantes. Une ou plusieurs de ces valeurs, séparées par des espaces (et non par des virgules), spécifient la liste des paramètres de la fonction. Les valeurs possibles sont répertoriées avec la macro [EVENT_CUSTOM](event-maps.md#event_custom) .

Cette fonction convertit les paramètres VARIANTARG valeurs, puis appelle la [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) (méthode). Si l’appel à `Invoke` échoue, cette fonction lève une exception. Si le SCODE (code d’état) retourné par `IDispatch::Invoke` est DISP_E_EXCEPTION, cette fonction lève un [COleException](../../mfc/reference/coleexception-class.md) ; sinon, elle lève une [COleDispatchException](../../mfc/reference/coledispatchexception-class.md).

Pour plus d’informations, consultez [VARIANTARG](/windows/desktop/api/oaidl/ns-oaidl-tagvariant), [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface), [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke), et [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) dans le Kit de développement logiciel Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::CreateDispatch](#createdispatch).

##  <a name="m_bautorelease"></a>  COleDispatchDriver::m_bAutoRelease

Si la valeur est TRUE, l’objet COM accessible par [sur m_lpDispatch](#m_lpdispatch) est automatiquement libérée lorsque [ReleaseDispatch](#releasedispatch) est appelée ou quand cela `COleDispatchDriver` objet est détruit.

```
BOOL m_bAutoRelease;
```

### <a name="remarks"></a>Notes

Par défaut, `m_bAutoRelease` est définie sur TRUE dans le constructeur.

Pour plus d’informations sur la libération d’objets COM, consultez [mise en œuvre un comptage de références](/windows/desktop/com/implementing-reference-counting) et [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#9](../../mfc/codesnippet/cpp/coledispatchdriver-class_5.cpp)]

##  <a name="m_lpdispatch"></a>  COleDispatchDriver::m_lpDispatch

Le pointeur vers le `IDispatch` interface attachée à ce `COleDispatchDriver`.

```
LPDISPATCH m_lpDispatch;
```

### <a name="remarks"></a>Notes

Le `m_lpDispatch` membre de données est une variable publique de type LPDISPATCH.

Pour plus d’informations, consultez [IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface) dans le SDK Windows.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::AttachDispatch](#attachdispatch).

##  <a name="operator_eq"></a>  COleDispatchDriver::operator =

Copie la valeur de la source dans le `COleDispatchDriver` objet.

```
const COleDispatchDriver& operator=(const COleDispatchDriver& dispatchSrc);
```

### <a name="parameters"></a>Paramètres

*dispatchSrc*<br/>
Un pointeur vers un existant `COleDispatchDriver` objet.

##  <a name="operator_lpdispatch"></a>  COleDispatchDriver::operator LPDISPATCH

Accède à sous-jacent `IDispatch` pointeur de la `COleDispatchDriver` objet.

```
operator LPDISPATCH();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#8](../../mfc/codesnippet/cpp/coledispatchdriver-class_6.cpp)]

##  <a name="releasedispatch"></a>  COleDispatchDriver::ReleaseDispatch

Versions le `IDispatch` connexion. Pour plus d’informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface)

```
void ReleaseDispatch();
```

### <a name="remarks"></a>Notes

Si la libération automatique a été définie pour cette connexion, cette fonction appelle `IDispatch::Release` avant de libérer de l’interface.

### <a name="example"></a>Exemple

  Consultez l’exemple de [COleDispatchDriver::AttachDispatch](#attachdispatch).

##  <a name="setproperty"></a>  COleDispatchDriver::SetProperty

Définit la propriété d’objet OLE spécifiée par *dwDispID*.

```
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
Un seul paramètre de type spécifié par *vtProp*.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCOleContainer#7](../../mfc/codesnippet/cpp/coledispatchdriver-class_7.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[Exemple MFC ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)

---
title: Débogage et déclaration d’erreurs Fonctions mondiales
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330204"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Débogage et déclaration d’erreurs Fonctions mondiales

Ces fonctions fournissent des installations de débogage et de traces utiles.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Retourne `GetLastError` un code d’erreur sous la forme d’un HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Convertit un code d'erreur Win32 en valeur HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Définit `IErrorInfo` pour fournir des détails d’erreur à un client.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Lève un `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Appelez cette fonction pour signaler une erreur en fonction du résultat de la fonction Windows `GetLastError`.|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHresultDeLastError

Retourne la dernière valeur du code d'erreur du thread appelant sous la forme d'une valeur HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Notes

`AtlHresultFromLastError`appels `GetLastError` pour obtenir la dernière erreur et renvoie l’erreur après la conversion en HRESULT en utilisant la macro HRESULT_FROM_WIN32.

### <a name="requirements"></a>Spécifications

**En-tête:** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultDeWin32

Convertit un code d'erreur Win32 en valeur HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Paramètres

*error*<br/>
La valeur d’erreur à convertir.

### <a name="remarks"></a>Notes

Convertit un code d’erreur Win32 en HRESULT, en utilisant la macro HRESULT_FROM_WIN32.

> [!NOTE]
> Au lieu `HRESULT_FROM_WIN32(GetLastError())`d’utiliser , utilisez la fonction [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Spécifications

**En-tête:** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>AtlReportError (en anglais)

Définit l’interface `IErrorInfo` pour fournir des informations d’erreur aux clients de l’objet.

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[dans] Le CLSID de l’objet signalant l’erreur.

*lpszDesc (en)*<br/>
[dans] La chaîne décrivant l’erreur. Les versions Unicode spécifient que *lpszDesc* est de type LPCOLESTR; la version ANSI spécifie un type de LPCSTR.

*Iid*<br/>
[dans] L’IID de l’interface définissant l’erreur ou GUID_NULL si l’erreur est définie par le système d’exploitation.

*hRes*<br/>
[dans] Le HRESULT que vous souhaitez retourner à l’appelant.

*nID*<br/>
[dans] L’identifiant de ressource où la chaîne de description d’erreur est stockée. Cette valeur devrait se situer entre 0x0200 et 0xFFFF, inclusivement. Dans les constructions de débogé, un **ASSERT** se traduira si *nID* n’indexe pas une chaîne valide. Dans les versions, la chaîne de description d’erreur sera définie à "Erreur inconnue."

*dwHelpID*<br/>
[dans] L’identifiant de contexte d’aide pour l’erreur.

*lpszHelpFile*<br/>
[dans] Le chemin et le nom du fichier d’aide décrivant l’erreur.

*hInst*<br/>
[dans] Le manche de la ressource. Par défaut, ce `__AtlBaseModuleModule::GetResourceInstance`paramètre est , où `__AtlBaseModuleModule` est l’exemple global de [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) ou une classe dérivée de lui.

### <a name="return-value"></a>Valeur de retour

Si le *paramètre hRes* est nonzero, retourne la valeur de *hRes*. Si *hRes* est zéro, alors les `AtlReportError` quatre premières versions de retour DISP_E_EXCEPTION. Les deux dernières versions renvoient le résultat de la macro **MAKE_HRESULT( 1, FACILITY_ITF,** `nID` **)**.

### <a name="remarks"></a>Notes

La chaîne *lpszDesc* est utilisée comme description textuelle de l’erreur. Lorsque le client reçoit les `AtlReportError` *hRes de* votre `IErrorInfo` retour, le client peut accéder à la structure pour plus de détails sur l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> N’utilisez `AtlReportError` pas dans les préposés aux captures de CMD. Certains remplacements de ces fonctions utilisent les macros de conversion `_alloca` de chaîne ATL en interne, qui à leur tour utilisent la fonction en interne. L’utilisation `AtlReportError` d’un gestionnaire de captures CMD peut entraîner des exceptions dans les préposés aux captures de CMD.

### <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow (en)

Appelez cette fonction pour signaler une erreur basée sur un code d’état HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Paramètres

*Hr*<br/>
Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par le code ATL et MFC en cas de condition d’erreur. Il peut également être appelé à partir de votre propre code. La mise en œuvre par défaut de cette fonction dépend de la définition du symbole _ATL_NO_EXCEPTIONS et du type de projet, MFC ou ATL.

Dans tous les cas, cette fonction retrace le HRESULT au débbugger.

Dans Visual Studio 2015 Mise à jour 3 et plus tard, cette fonction est attribuée __declspec (noreturn) pour éviter les avertissements SAL faux.

Si _ATL_NO_EXCEPTIONS n’est pas définie dans un projet MFC, cette fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou un [COleException](../../mfc/reference/coleexception-class.md) basé sur la valeur de la HRESULT.

Si _ATL_NO_EXCEPTIONS n’est pas définie dans un projet ATL, la fonction jette un [CAtlException](../../atl/reference/catlexception-class.md).

Si _ATL_NO_EXCEPTIONS est définie, la fonction provoque une défaillance d’affirmation au lieu de jeter une exception.

Pour les projets ATL, il est possible de fournir votre propre mise en œuvre de cette fonction à utiliser par ATL en cas de défaillance. Pour ce faire, définissez votre propre `AtlThrow` fonction avec `AtlThrow` la même signature que et #define d’être le nom de votre fonction. Cela doit être fait avant d’inclure atlexcept.h (ce qui signifie qu’il doit être fait avant d’inclure les en-têtes ATL depuis atlbase.h comprend atlexcept.h). Attribuez `__declspec(noreturn)` votre fonction pour éviter les avertissements SAL faux.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Spécifications

**En-tête:** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Appelez cette fonction pour signaler une erreur en fonction du résultat de la fonction Windows `GetLastError`.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Notes

Cette fonction trace le `GetLastError` résultat du débbuggeur.

Si _ATL_NO_EXCEPTIONS n’est pas définie dans un projet MFC, cette fonction jette un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) `GetLastError`ou un [COleException](../../mfc/reference/coleexception-class.md) basé sur la valeur retournée par .

Si _ATL_NO_EXCEPTIONS n’est pas définie dans un projet ATL, la fonction jette un [CAtlException](../../atl/reference/catlexception-class.md).

Si _ATL_NO_EXCEPTIONS est définie, la fonction provoque une défaillance d’affirmation au lieu de jeter une exception.

## <a name="requirements"></a>Spécifications

**En-tête:** atldef.h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de débogage et de déclaration d’erreurs](../../atl/reference/debugging-and-error-reporting-macros.md)

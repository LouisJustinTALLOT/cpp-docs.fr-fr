---
title: Fonctions globales de débogage et de rapport d’erreurs
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7483b7473383958089b0c88d0b3c2645ddc2a4f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417711"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Fonctions globales de débogage et de rapport d’erreurs

Ces fonctions fournissent des fonctionnalités de débogage et de suivi utiles.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Retourne un `GetLastError` code d’erreur sous la forme d’un HRESULT.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Convertit un code d'erreur Win32 en valeur HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Configure `IErrorInfo` pour fournir des détails d’erreur à un client.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Lève un `CAtlException`.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Appelez cette fonction pour signaler une erreur en fonction du résultat de la fonction Windows `GetLastError`.|

##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

Retourne la dernière valeur du code d'erreur du thread appelant sous la forme d'une valeur HRESULT.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Notes

`AtlHresultFromLastError` appelle `GetLastError` pour obtenir la dernière erreur et retourne l’erreur après la conversion en HRESULT à l’aide de la macro HRESULT_FROM_WIN32.

### <a name="requirements"></a>Spécifications

**En-tête :** atlcomcli. h

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32

Convertit un code d'erreur Win32 en valeur HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Paramètres

*error*<br/>
Valeur d’erreur à convertir.

### <a name="remarks"></a>Notes

Convertit un code d’erreur Win32 en HRESULT, à l’aide de la macro HRESULT_FROM_WIN32.

> [!NOTE]
>  Au lieu d’utiliser `HRESULT_FROM_WIN32(GetLastError())`, utilisez la fonction [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Spécifications

**En-tête :** atlcomcli. h

##  <a name="atlreporterror"></a>AtlReportError

Configure l’interface `IErrorInfo` pour fournir des informations d’erreur aux clients de l’objet.

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

*identificateur*<br/>
dans CLSID de l’objet qui signale l’erreur.

*lpszDesc*<br/>
dans Chaîne décrivant l’erreur. Les versions Unicode spécifient que *lpszDesc* est de type LPCOLESTR ; la version ANSI spécifie un type de LPCSTR.

*vaut*<br/>
dans IID de l’interface définissant l’erreur ou GUID_NULL si l’erreur est définie par le système d’exploitation.

*hRes*<br/>
dans HRESULT que vous souhaitez retourner à l’appelant.

*nID*<br/>
dans Identificateur de ressource dans lequel la chaîne de description de l’erreur est stockée. Cette valeur doit être comprise entre 0x0200 et 0xFFFF, inclus. Dans les versions Debug, une **assertion** se produit si *nid* n’indexe pas une chaîne valide. Dans les versions release, la chaîne de description d’erreur est définie sur « erreur inconnue ».

*dwHelpID*<br/>
dans Identificateur du contexte d’aide pour l’erreur.

*lpszHelpFile*<br/>
dans Chemin d’accès et nom du fichier d’aide décrivant l’erreur.

*hInst*<br/>
dans Handle de la ressource. Par défaut, ce paramètre est `__AtlBaseModuleModule::GetResourceInstance`, où `__AtlBaseModuleModule` est l’instance globale de [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) ou une classe dérivée de celui-ci.

### <a name="return-value"></a>Valeur de retour

Si le paramètre *hres* est différent de zéro, retourne la valeur de *hres*. Si *hres* est égal à zéro, les quatre premières versions de `AtlReportError` retournent DISP_E_EXCEPTION. Les deux dernières versions renvoient le résultat de la macro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)** .

### <a name="remarks"></a>Notes

La chaîne *lpszDesc* est utilisée comme description textuelle de l’erreur. Lorsque le client reçoit le *hres* que vous retournez de `AtlReportError`, le client peut accéder à la structure `IErrorInfo` pour plus d’informations sur l’erreur.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
>  N’utilisez pas `AtlReportError` dans C++ les gestionnaires catch. Certaines substitutions de ces fonctions utilisent les macros de conversion de chaînes ATL en interne, qui à leur tour utilisent la fonction `_alloca` en interne. L’utilisation de `AtlReportError` C++ dans un gestionnaire catch peut provoquer C++ des exceptions dans les gestionnaires catch.

### <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

##  <a name="atlthrow"></a>AtlThrow

Appelez cette fonction pour signaler une erreur en fonction d’un code d’État HRESULT.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Paramètres

*h*<br/>
Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Cette fonction est utilisée par ATL et le code MFC dans le cas d’une condition d’erreur. Elle peut également être appelée à partir de votre propre code. L’implémentation par défaut de cette fonction dépend de la définition du symbole _ATL_NO_EXCEPTIONS et du type de projet, MFC ou ATL.

Dans tous les cas, cette fonction effectue le suivi de HRESULT au débogueur.

Dans Visual Studio 2015 Update 3 et versions ultérieures, cette fonction est attribuée __declspec (noreturn) pour éviter les fausses alertes SAL.

Si _ATL_NO_EXCEPTIONS n’est pas défini dans un projet MFC, cette fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou un [COleException](../../mfc/reference/coleexception-class.md) en fonction de la valeur de HRESULT.

Si _ATL_NO_EXCEPTIONS n’est pas défini dans un projet ATL, la fonction lève une [CAtlException](../../atl/reference/catlexception-class.md).

Si _ATL_NO_EXCEPTIONS est défini, la fonction provoque un échec d’assertion au lieu de lever une exception.

Pour les projets ATL, il est possible de fournir votre propre implémentation de cette fonction pour qu’elle soit utilisée par ATL en cas d’échec. Pour ce faire, définissez votre propre fonction avec la même signature que `AtlThrow` et #define `AtlThrow` en tant que nom de votre fonction. Cela doit être fait avant d’inclure atlexcept. h (ce qui signifie qu’il doit être fait avant d’inclure des en-têtes ATL, car atlbase. h inclut atlexcept. h). Attributez votre fonction `__declspec(noreturn)` pour éviter les fausses avertissements SAL.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Spécifications

**En-tête :** atldef. h

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Appelez cette fonction pour signaler une erreur en fonction du résultat de la fonction Windows `GetLastError`.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Notes

Cette fonction suit le résultat de `GetLastError` au débogueur.

Si _ATL_NO_EXCEPTIONS n’est pas défini dans un projet MFC, cette fonction lève une [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou un [COleException](../../mfc/reference/coleexception-class.md) en fonction de la valeur retournée par `GetLastError`.

Si _ATL_NO_EXCEPTIONS n’est pas défini dans un projet ATL, la fonction lève une [CAtlException](../../atl/reference/catlexception-class.md).

Si _ATL_NO_EXCEPTIONS est défini, la fonction provoque un échec d’assertion au lieu de lever une exception.

## <a name="requirements"></a>Spécifications

**En-tête :** atldef. h

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)<br/>
[Macros de signalement d’erreurs et de débogage](../../atl/reference/debugging-and-error-reporting-macros.md)

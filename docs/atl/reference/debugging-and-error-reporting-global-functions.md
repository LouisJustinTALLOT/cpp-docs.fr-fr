---
title: Fonctions globales de signalement d’erreurs et de débogage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs:
- C++
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb3257b5205587b27a83671ed8e610aad5373eef
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364880"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Fonctions globales de signalement d’erreurs et de débogage
Ces fonctions fournissent des fonctionnalités de débogage et le traçage utiles.  
  
|||  
|-|-|  
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Retourne un `GetLastError` code d’erreur sous la forme d’une valeur HRESULT.|  
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Convertit un code d'erreur Win32 en valeur HRESULT.|  
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Configure **IErrorInfo** pour fournir des détails de l’erreur à un client.|  
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Lève un `CAtlException`.|  
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Appelez cette fonction pour signaler une erreur en fonction du résultat de la fonction Windows `GetLastError`.|  
  
##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError  
 Retourne la dernière valeur du code d'erreur du thread appelant sous la forme d'une valeur HRESULT.  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>Notes  
 `AtlHresultFromLastError` appels `GetLastError` pour obtenir la dernière erreur et retourne l’erreur après sa conversion en un HRESULT à l’aide de la **HRESULT_FROM_WIN32** (macro).  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32  
 Convertit un code d'erreur Win32 en valeur HRESULT.  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>Paramètres  
 *Erreur*  
 La valeur d’erreur à convertir.  
  
### <a name="remarks"></a>Notes  
 Convertit un code d’erreur Win32 en valeur HRESULT, à l’aide de la macro **HRESULT_FROM_WIN32**.  
  
> [!NOTE]
>  Au lieu d’utiliser **HRESULT_FROM_WIN32(GetLastError())**, utilisez la fonction [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlcomcli.h  

##  <a name="atlreporterror"></a>  AtlReportError  
 Configure le `IErrorInfo` interface pour fournir des informations d’erreur aux clients de l’objet.  
  
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
 `clsid`  
 [in] Le CLSID de l’objet qui signale l’erreur.  
  
 `lpszDesc`  
 [in] Chaîne décrivant l’erreur. Les versions Unicode spécifient que `lpszDesc` est de type **LPCOLESTR**; la version ANSI spécifie un type de `LPCSTR`.  
  
 `iid`  
 [in] IID de l’interface qui définit l’erreur ou `GUID_NULL` si l’erreur est définie par le système d’exploitation.  
  
 `hRes`  
 [in] Le `HRESULT` à renvoyer à l’appelant.  
  
 `nID`  
 [in] L’identificateur de ressource où se trouve la chaîne de description d’erreur. Cette valeur doit être comprise entre 0 x 0200 et 0xFFFF, inclus. Dans les versions debug, un **ASSERT** se produira si `nID` n’indexe pas une chaîne valide. Dans les versions release, la chaîne de description d’erreur sera définie sur « Erreur inconnue ».  
  
 `dwHelpID`  
 [in] L’identificateur de contexte d’aide pour l’erreur.  
  
 `lpszHelpFile`  
 [in] Le chemin d’accès et le nom du fichier d’aide décrivant l’erreur.  
  
 `hInst`  
 [in] Le handle de la ressource. Par défaut, ce paramètre est **__AtlBaseModuleModule::GetResourceInstance**, où **__AtlBaseModuleModule** est l’instance globale de [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) ou une classe dérivée de celle-ci.  
  
### <a name="return-value"></a>Valeur de retour  
 Si le `hRes` paramètre est différent de zéro, retourne la valeur de `hRes`. Si `hRes` est zéro, les quatre premières versions de `AtlReportError` retourner `DISP_E_EXCEPTION`. Les deux dernières versions retournent le résultat de la macro **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
### <a name="remarks"></a>Notes  
 La chaîne *lpszDesc* est utilisé en tant que la description de l’erreur. Lorsque le client reçoit la `hRes` retour de `AtlReportError`, le client peut accéder à la **IErrorInfo** structure pour plus d’informations sur l’erreur.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  N’utilisez pas `AtlReportError` dans C++ gestionnaires catch. Certaines substitutions de ces fonctions d’utiliser les macros de conversion de chaînes ATL en interne, qui à son tour le `_alloca` fonctionnent en interne. À l’aide de `AtlReportError` dans un bloc catch C++ gestionnaire peut provoquer des exceptions dans les gestionnaires catch C++.  

### <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
    
##  <a name="atlthrow"></a>  AtlThrow  
 Appelez cette fonction pour signaler une erreur en fonction d'un code d'état `HRESULT`.  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>Paramètres  
 `hr`  
 Valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est utilisée par le code ATL et MFC en cas d’une condition d’erreur. Il peut également être appelée à partir de votre propre code. L’implémentation par défaut de cette fonction dépend de la définition du symbole **_ATL_NO_EXCEPTIONS** et sur le type de projet, MFC ou ATL.  
  
 Dans tous les cas, cette fonction suit la valeur HRESULT au débogueur.  
  
 Dans Visual Studio 2015 Update 3 et versions ultérieures, cette fonction est attribué __declspec (noreturn) afin d’éviter les fausses avertissements SAL.  
  
 Si **_ATL_NO_EXCEPTIONS** n’est pas défini dans un projet MFC, cette fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou un [COleException](../../mfc/reference/coleexception-class.md) selon la valeur de la valeur HRESULT.  
  
 Si **_ATL_NO_EXCEPTIONS** n’est pas défini dans un projet ATL, la fonction lève un [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Si **_ATL_NO_EXCEPTIONS** est défini, la fonction provoque un échec d’assertion au lieu de lever une exception.  
  
 Pour les projets ATL, il est possible de fournir votre propre implémentation de cette fonction doit utiliser ATL en cas de défaillance. Pour ce faire, définissez votre propre fonction avec la même signature que `AtlThrow` et #define `AtlThrow` par le nom de votre fonction. Ceci doit être fait avant d’inclure atlexcept.h (ce qui signifie qu’il doit être exécuté avant d’inclure des en-têtes ATL atlbase.h incluant atlexcept.h). Attribut de votre fonction `__declspec(noreturn)` afin d’éviter les fausses avertissements SAL.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atldef.h  

##  <a name="atlthrowlastwin32"></a>  AtlThrowLastWin32  
 Appelez cette fonction pour signaler une erreur en fonction du résultat de la fonction Windows `GetLastError`.  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction effectue le suivi du résultat de `GetLastError` au débogueur.  
  
 Si **_ATL_NO_EXCEPTIONS** n’est pas défini dans un projet MFC, cette fonction lève un [CMemoryException](../../mfc/reference/cmemoryexception-class.md) ou un [COleException](../../mfc/reference/coleexception-class.md) selon la valeur retournée par `GetLastError`.  
  
 Si **_ATL_NO_EXCEPTIONS** n’est pas défini dans un projet ATL, la fonction lève un [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Si **_ATL_NO_EXCEPTIONS** est défini, la fonction provoque un échec d’assertion au lieu de lever une exception.  

## <a name="requirements"></a>Spécifications  
 **En-tête :** atldef.h  
   
     
## <a name="see-also"></a>Voir aussi  
 [Fonctions](../../atl/reference/atl-functions.md)   
 [Macros de signalement d’erreurs et de débogage](../../atl/reference/debugging-and-error-reporting-macros.md)










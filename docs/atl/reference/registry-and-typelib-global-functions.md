---
title: Fonctions globales du Registre et de TypeLib | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlGetPerUserRegistration
- afxpriv/ATL::AfxRegCreateKey
- afxpriv/ATL::AfxRegDeleteKey
- atlbase/ATL::AtlRegisterTypeLib
- afxpriv/ATL::AfxRegOpenKey
- afxpriv/ATL::AfxRegOpenKeyEx
- afxdisp/ATL::AfxUnregisterPreviewHandler
- atlbase/ATL::AtlSetPerUserRegistration
- atlbase/ATL::AtlUnRegisterTypeLib
- atlbase/ATL::AtlLoadTypeLib
- atlbase/ATL::AtlUpdateRegistryFromResourceD
- atlbase/ATL::RegistryDataExchange
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84328c35ceb9a4cf2631f27e9f860a1f60e33c55
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885413"
---
# <a name="registry-and-typelib-global-functions"></a>Fonctions globales du Registre et de TypeLib
Ces fonctions fournissent la prise en charge pour le chargement et l’inscription d’une bibliothèque de types.  
  
> [!IMPORTANT]
>  Les fonctions répertoriées dans les tableaux suivants ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
|||  
|-|-|  
|[AfxRegCreateKey](#afxrefcreatekey)|Crée la clé de Registre spécifiée.|
|[AfxRegDeleteKey](#afxrefdeletekey)|Supprime la clé de Registre spécifiée.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Un programme d’assistance pour inscrire un gestionnaire d’aperçus.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Un programme d’assistance pour annuler l’inscription d’un gestionnaire d’aperçus. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Cette fonction est appelée pour inscrire une bibliothèque de types.|  
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Cette fonction est appelée pour annuler l’inscription d’une bibliothèque de types|  
|[AfxRegOpenKey](#afxregopenkey)|Ouvre la clé de Registre spécifiée.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Ouvre la clé de Registre spécifiée.|
|[AtlLoadTypeLib](#atlloadtypelib)|Cette fonction est appelée pour charger une bibliothèque de types.|  
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Cette fonction est appelée pour mettre à jour le Registre à partir de la ressource fournie.|  
|[RegistryDataExchange](#registrydataexchange)|Cette fonction est appelée pour lire ou écrire dans le Registre système. Appelé par le [Macros d’échange de données de Registre](../../atl/reference/registry-data-exchange-macros.md).|  
  
 Ces fonctions contrôlent quel nœud dans le Registre, le programme utilise pour stocker les informations.  
  
|||  
|-|-|  
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Récupère si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** ( **HKCU**) nœud.|  
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Définit si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** ( **HKCU**) nœud.|  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h

## <a name="atlgetperuserregistration"></a> AtlGetPerUserRegistration
Utilisez cette fonction pour déterminer si l’application redirige l’accès au Registre pour le **HKEY_CURRENT_USER** (**HKCU**) nœud.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *pEnabled*  
 TRUE indique que les informations du Registre sont dirigées vers le **HKCU** nœud ; La valeur FALSE indique que l’application écrit les informations du Registre pour le nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussite, sinon l’erreur HRESULT du code si une erreur se produit.  
  
### <a name="remarks"></a>Notes  
 La redirection du Registre n’est pas activée par défaut. Si vous activez cette option, l’accès au Registre est redirigé vers **HKEY_CURRENT_USER\Software\Classes**.  
  
 La redirection n’est pas globale. Uniquement les infrastructures MFC et ATL sont affectés par cette redirection de Registre.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  

 ## <a name="afxregcreatekey"></a> AfxRegCreateKey
 Crée la clé de Registre spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *clé hKey*  
 Handle vers une clé de Registre ouverte.  
  
 *lpSubKey*  
 Le nom d’une clé de cette fonction ouvre ou crée.  
  
 *phkResult*  
 Pointeur vers une variable qui reçoit un handle à la clé ouvert ou créé.  
  
 *pTM*  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror.h.  

### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpriv.h  

## <a name="afxregdeletekey"></a> AfxRegDeleteKey
Supprime la clé de Registre spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *clé hKey*  
 Handle vers une clé de Registre ouverte.  
  
 *lpSubKey*  
 Le nom de la clé à supprimer.  
  
 *pTM*  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror.h.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpriv.h  

## <a name="afxregisterpreviewhandler"></a>
Un programme d’assistance pour inscrire un gestionnaire d’aperçus.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszCLSID*  
 Spécifie le CLSID du gestionnaire.  
  
 *lpszShortTypeName*  
 Spécifie le ProgID du gestionnaire.  
  
 *lpszFilterExt*  
 Spécifie l’extension de fichier enregistrée avec ce gestionnaire.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdisp.h   

##  <a name="atlregistertypelib"></a>  AtlRegisterTypeLib  
 Cette fonction est appelée pour inscrire une bibliothèque de types.  
  
  
```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstTypeLib*  
 Handle de l’instance de module.  
  
 *lpszIndex*  
 Chaîne au format «\\\N », où N est l’index d’entier de la ressource de bibliothèque de type. Peut d’être NULL si aucun index n’est requis.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction d’assistance utilisée par [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) et [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h

 ## <a name="afxregopenkey"></a> AfxRegOpenKey
 Ouvre la clé de Registre spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *clé hKey*  
 Handle vers une clé de Registre ouverte.  
  
 *lpSubKey*  
 Le nom d’une clé de cette fonction ouvre ou crée.  
  
 *phkResult*  
 Pointeur vers une variable qui reçoit un handle vers la clé créée.  
  
 *pTM*  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror.h.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpriv.h  

## <a name="afxregopenkeyex"></a>  AfxRegOpenKeyEx
Ouvre la clé de Registre spécifiée. 

### <a name="syntax"></a>Syntaxe  
  
```  
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);  
```  
  
### <a name="parameters"></a>Paramètres  
 *clé hKey*  
 Handle vers une clé de Registre ouverte.  
  
 *lpSubKey*  
 Le nom d’une clé de cette fonction ouvre ou crée.  
  
 *ulOptions*  
 Ce paramètre est réservé et doit être égal à zéro.  
  
 *samDesired*  
 Masque qui spécifie les droits d’accès souhaité à la clé.  
  
 *phkResult*  
 Pointeur vers une variable qui reçoit un handle à la clé ouvert.  
  
 *pTM*  
 Pointeur vers un `CAtlTransactionManager` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror.h.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpriv.h  

 ## <a name="afxunregisterpreviewhandler"></a> AfxUnregisterPreviewHandler
 Un programme d’assistance pour annuler l’inscription d’un gestionnaire d’aperçus.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszCLSID*  
 Spécifie le CLSID du gestionnaire doit être annulée.  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** afxdisp.h  

## <a name="atlsetperuserregistration"></a> AtlSetPerUserRegistration
Définit si l’application redirige l’accès au Registre vers le **HKEY_CURRENT_USER** (**HKCU**) nœud.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActivez*  
 TRUE indique que les informations du Registre sont dirigées vers le **HKCU** nœud ; La valeur FALSE indique que l’application écrit les informations du Registre pour le nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).  
  
### <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussite, sinon l’erreur HRESULT du code si une erreur se produit.  
  
### <a name="remarks"></a>Notes  
 La redirection du Registre n’est pas activée par défaut. Si vous activez cette option, l’accès au Registre est redirigé vers **HKEY_CURRENT_USER\Software\Classes**.  
  
 La redirection n’est pas globale. Uniquement les infrastructures MFC et ATL sont affectés par cette redirection de Registre.  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  

##  <a name="atlunregistertypelib"></a>  AtlUnRegisterTypeLib  
 Cette fonction est appelée pour annuler l'inscription d'une bibliothèque de types.  
  
### <a name="syntax"></a>Syntaxe  
```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib, 
    LPCOLESTR lpszIndex);
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstTypeLib*  
 Handle de l’instance de module.  
  
 *lpszIndex*  
 Chaîne au format «\\\N », où N est l’index d’entier de la ressource de bibliothèque de type. Peut d’être NULL si aucun index n’est requis.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction d’assistance utilisée par [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) et [AtlComModuleUnregisterServer](#atlcommoduleunregisterserver).  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h

##  <a name="atlloadtypelib"></a>  AtlLoadTypeLib  
 Cette fonction est appelée pour charger une bibliothèque de types.  
  
### <a name="syntax"></a>Syntaxe  
```
ATLINLINE ATLAPI AtlLoadTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex,
    BSTR* pbstrPath,
    ITypeLib** ppTypeLib);
```  
  
### <a name="parameters"></a>Paramètres  
 *hInstTypeLib*  
 Handle vers le module associé à la bibliothèque de types.  
  
 *lpszIndex*  
 Chaîne au format «\\\N », où N est l’index d’entier de la ressource de bibliothèque de type. Peut d’être NULL si aucun index n’est requis.  
  
 *pbstrPath*  
 Lors d’un retour, contient le chemin d’accès complet du module associé à la bibliothèque de types.  
  
 *ppTypeLib*  
 Lors d’un retour, contient un pointeur vers un pointeur vers la bibliothèque de types chargés.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette fonction d’assistance utilisée par [AtlRegisterTypeLib](#atlregistertypelib) et [AtlUnRegisterTypeLib](#atlunregistertypelib).  
  
##  <a name="atlupdateregistryfromresourced"></a>  AtlUpdateRegistryFromResourceD  
 Cette fonction a été déconseillée dans Visual Studio 2013 et supprimée dans Visual Studio 2015.  
  
```
<removed>
```  
  

  
##  <a name="registrydataexchange"></a>  RegistryDataExchange  
 Cette fonction est appelée pour lire ou écrire dans le Registre système.  

### <a name="syntax"></a>Syntaxe  
```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 *pT*  
 Pointeur vers l’objet actuel.  
  
 *rdxOp*  
 Une valeur d’énumération qui indique quelle opération la fonction doit effectuer. Consultez le tableau dans la section Notes pour les valeurs autorisées.  
  
 *pItem*  
 Pointeur vers les données qui doit être lues ou écrites dans le Registre. Les données peuvent également représenter une clé à supprimer à partir du Registre. La valeur par défaut est NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Les macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) et [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) développez à une fonction qui appelle `RegistryDataExchange`.  
  
 Les valeurs enum possibles qui indiquent que l’opération la fonction doit effectuer sont affichées dans le tableau suivant :  
  
|Valeur enum|Opération|  
|----------------|---------------|  
|eReadFromReg|Lire les données à partir du Registre.|  
|eWriteToReg|Écrire des données dans le Registre.|  
|eDeleteFromReg|Supprimer la clé du Registre.|  
  
### <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h

## <a name="see-also"></a>Voir aussi  
 [Fonctions](atl-functions.md) [Macros d’échange de données de Registre](registry-data-exchange-macros.md)






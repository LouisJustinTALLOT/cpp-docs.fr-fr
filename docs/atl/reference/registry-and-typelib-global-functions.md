---
title: Fonctions globales du Registre et de TypeLib
ms.date: 03/27/2019
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
helpviewer_keywords:
- RegistryDataExchange function, global functions
ms.assetid: d58b8a4e-975c-4417-8b34-d3c847f679b3
ms.openlocfilehash: c5fdaceb47b6cd09dd9d66f26af1337a8dc6bbae
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417494"
---
# <a name="registry-and-typelib-global-functions"></a>Fonctions globales du Registre et de TypeLib

Ces fonctions prennent en charge le chargement et l’inscription d’une bibliothèque de types.

> [!IMPORTANT]
>  Les fonctions listées dans les tableaux suivants ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Crée la clé de Registre spécifiée.|
|[AfxRegDeleteKey](#afxregdeletekey)|Supprime la clé de Registre spécifiée.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Une application d’assistance pour inscrire un gestionnaire d’aperçus.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Une application d’assistance pour annuler l’inscription d’un gestionnaire d’aperçus. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Cette fonction est appelée pour inscrire une bibliothèque de types.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Cette fonction est appelée pour annuler l’inscription d’une bibliothèque de types|
|[AfxRegOpenKey](#afxregopenkey)|Ouvre la clé de Registre spécifiée.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Ouvre la clé de Registre spécifiée.|
|[AtlLoadTypeLib](#atlloadtypelib)|Cette fonction est appelée pour charger une bibliothèque de types.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Cette fonction est appelée pour mettre à jour le Registre à partir de la ressource fournie.|
|[RegistryDataExchange](#registrydataexchange)|Cette fonction est appelée pour lire ou écrire dans le Registre système. Appelée par les [macros d’échange de données du Registre](../../atl/reference/registry-data-exchange-macros.md).|

Ces fonctions contrôlent le nœud du registre utilisé par le programme pour stocker des informations.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Récupère si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** ( **HKCU**).|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Définit si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** ( **HKCU**).|

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Utilisez cette fonction pour déterminer si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Paramètres

*pEnabled*<br/>
à La valeur TRUE indique que les informations du Registre sont dirigées vers le nœud **HKCU** . La valeur FALSe indique que l’application écrit les informations du Registre dans le nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode est réussie, sinon le code d’erreur HRESULT si une erreur se produit.

### <a name="remarks"></a>Notes

La redirection du Registre n’est pas activée par défaut. Si vous activez cette option, l’accès au registre est redirigé vers **HKEY_CURRENT_USER \Software\Classes**.

La redirection n’est pas globale. Seules les infrastructures MFC et ATL sont affectées par cette redirection du Registre.

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="afxregcreatekey"></a>AfxRegCreateKey

Crée la clé de Registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de Registre ouverte.

*lpSubKey*<br/>
Nom d’une clé que cette fonction ouvre ou crée.

*phkResult*<br/>
Pointeur vers une variable qui reçoit un handle vers la clé ouverte ou créée.

*pTM*<br/>
Pointeur vers un objet `CAtlTransactionManager`.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxregdeletekey"></a>AfxRegDeleteKey

Supprime la clé de Registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de Registre ouverte.

*lpSubKey*<br/>
Nom de la clé à supprimer.

*pTM*<br/>
Pointeur vers un objet `CAtlTransactionManager`.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

Une application d’assistance pour inscrire un gestionnaire d’aperçus.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Paramètres

*lpszCLSID*<br/>
Spécifie le CLSID du gestionnaire.

*lpszShortTypeName*<br/>
Spécifie l’identificateur de programme (ProgID) du gestionnaire.

*lpszFilterExt*<br/>
Spécifie l’extension de fichier inscrite auprès de ce gestionnaire.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

##  <a name="atlregistertypelib"></a>AtlRegisterTypeLib

Cette fonction est appelée pour inscrire une bibliothèque de types.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Paramètres

*hInstTypeLib*<br/>
Handle de l’instance de module.

*lpszIndex*<br/>
Chaîne au format «\\\n », où N est l’index entier de la ressource de bibliothèque de types. Peut avoir la valeur NULL si aucun index n’est requis.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance est utilisée par [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) et [CAtlComModule :: RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="afxregopenkey"></a>AfxRegOpenKey

Ouvre la clé de Registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de Registre ouverte.

*lpSubKey*<br/>
Nom d’une clé que cette fonction ouvre ou crée.

*phkResult*<br/>
Pointeur vers une variable qui reçoit un handle vers la clé créée.

*pTM*<br/>
Pointeur vers un objet `CAtlTransactionManager`.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Ouvre la clé de Registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de Registre ouverte.

*lpSubKey*<br/>
Nom d’une clé que cette fonction ouvre ou crée.

*ulOptions*<br/>
Ce paramètre est réservé et doit être égal à zéro.

*samDesired*<br/>
Masque qui spécifie les droits d’accès souhaités à la clé.

*phkResult*<br/>
Pointeur vers une variable qui reçoit un handle vers la clé ouverte.

*pTM*<br/>
Pointeur vers un objet `CAtlTransactionManager`.

### <a name="return-value"></a>Valeur de retour

Si la fonction est réussie, la valeur de retour est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans Winerror. h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Une application d’assistance pour annuler l’inscription d’un gestionnaire d’aperçus.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Paramètres

*lpszCLSID*<br/>
Spécifie le CLSID du gestionnaire dont l’inscription doit être annulée.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

Définit si l’application redirige l’accès au registre vers le nœud **HKEY_CURRENT_USER** (**HKCU**).

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans La valeur TRUE indique que les informations du Registre sont dirigées vers le nœud **HKCU** . La valeur FALSe indique que l’application écrit les informations du Registre dans le nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode est réussie, sinon le code d’erreur HRESULT si une erreur se produit.

### <a name="remarks"></a>Notes

La redirection du Registre n’est pas activée par défaut. Si vous activez cette option, l’accès au registre est redirigé vers **HKEY_CURRENT_USER \Software\Classes**.

La redirection n’est pas globale. Seules les infrastructures MFC et ATL sont affectées par cette redirection du Registre.

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

##  <a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

Cette fonction est appelée pour annuler l'inscription d'une bibliothèque de types.

### <a name="syntax"></a>Syntaxe

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Paramètres

*hInstTypeLib*<br/>
Handle de l’instance de module.

*lpszIndex*<br/>
Chaîne au format «\\\n », où N est l’index entier de la ressource de bibliothèque de types. Peut avoir la valeur NULL si aucun index n’est requis.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance est utilisée par [CAtlComModule :: UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) et [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

##  <a name="atlloadtypelib"></a>AtlLoadTypeLib

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

*hInstTypeLib*<br/>
Handle vers le module associé à la bibliothèque de types.

*lpszIndex*<br/>
Chaîne au format «\\\n », où N est l’index entier de la ressource de bibliothèque de types. Peut avoir la valeur NULL si aucun index n’est requis.

*pbstrPath*<br/>
En cas de retour réussi, contient le chemin d’accès complet du module associé à la bibliothèque de types.

*ppTypeLib*<br/>
En cas de retour réussi, contient un pointeur vers un pointeur vers la bibliothèque de types chargée.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction d’assistance est utilisée par [AtlRegisterTypeLib](#atlregistertypelib) et [AtlUnRegisterTypeLib](#atlunregistertypelib).

##  <a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryFromResourceD

Cette fonction a été déconseillée dans Visual Studio 2013 et supprimée dans Visual Studio 2015.

```
<removed>
```

##  <a name="registrydataexchange"></a>RegistryDataExchange

Cette fonction est appelée pour lire ou écrire dans le Registre système.

### <a name="syntax"></a>Syntaxe

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Paramètres

*Unis*<br/>
Pointeur vers l’objet actuel.

*rdxOp*<br/>
Valeur enum qui indique l’opération que la fonction doit effectuer. Consultez le tableau dans la section Notes pour connaître les valeurs autorisées.

*pItem*<br/>
Pointeur vers les données à lire ou à écrire dans le registre. Les données peuvent également représenter une clé à supprimer du Registre. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Les macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) et [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) se développent jusqu’à une fonction qui appelle `RegistryDataExchange`.

Les valeurs d’énumération possibles qui indiquent l’opération que la fonction doit effectuer sont indiquées dans le tableau suivant :

|Valeur enum|Opération|
|----------------|---------------|
|eReadFromReg|Lire les données à partir du Registre.|
|eWriteToReg|Écrire des données dans le registre.|
|eDeleteFromReg|Supprimez la clé du Registre.|

### <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="see-also"></a>Voir aussi

[Fonctions](atl-functions.md)<br/>
[Macros d’échange de données de Registre](registry-data-exchange-macros.md)

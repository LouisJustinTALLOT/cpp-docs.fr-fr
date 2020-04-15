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
ms.openlocfilehash: 69df927ddd04c19d10703854aa8c8948894309d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326080"
---
# <a name="registry-and-typelib-global-functions"></a>Fonctions globales du Registre et de TypeLib

Ces fonctions fournissent un support pour le chargement et l’enregistrement d’une bibliothèque de type.

> [!IMPORTANT]
> Les fonctions énumérées dans les tableaux suivants ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AfxRegCreateKey](#afxregcreatekey)|Crée la clé de registre spécifiée.|
|[AfxRegDeleteKey](#afxregdeletekey)|Supprime la clé de registre spécifiée.|
|[AfxRegisterPreviewHandler](#afxregisterpreviewhandler)|Un assistant pour enregistrer un gestionnaire de prévisualisation.|
|[AfxUnregisterPreviewHandler](#afxunregisterpreviewhandler)| Un aide pour déenregistrer un gestionnaire de prévisualisation. |
|[AtlRegisterTypeLib](#atlregistertypelib)|Cette fonction est appelée pour inscrire une bibliothèque de types.|
|[AtlUnRegisterTypeLib](#atlunregistertypelib)|Cette fonction est appelée à désenregistrer une bibliothèque de type|
|[AfxRegOpenKey](#afxregopenkey)|Ouvre la clé de registre spécifiée.|
|[AfxRegOpenKeyEx](#afxregopenkeyex)|Ouvre la clé de registre spécifiée.|
|[AtlLoadTypeLib](#atlloadtypelib)|Cette fonction est appelée pour charger une bibliothèque de types.|
|[AtlUpdateRegistryFromResourceD](#atlupdateregistryfromresourced)|Cette fonction est appelée pour mettre à jour le Registre à partir de la ressource fournie.|
|[RegistryDataExchange](#registrydataexchange)|Cette fonction est appelée pour lire ou écrire dans le Registre système. Appelé par le [Registre Data Exchange Macros](../../atl/reference/registry-data-exchange-macros.md).|

Ces fonctions contrôlent le nœud dans le registre que le programme utilise pour stocker l’information.

|||
|-|-|
|[AtlGetPerUserRegistration](#atlgetperuserregistration)|Sais-la-demande redirige l’accès au registre vers le **nœud HKEY_CURRENT_USER** ( **HKCU).**|
|[AtlSetPerUserRegistration](#atlsetperuserregistration)|Définit si l’application redirige l’accès au registre vers le **nœud HKEY_CURRENT_USER** ( **HKCU).**|

### <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlgetperuserregistration"></a><a name="atlgetperuserregistration"></a>AtlGetPerUserRegistration

Utilisez cette fonction pour déterminer si l’application redirige l’accès au registre au **nœud HKEY_CURRENT_USER** (**HKCU).**

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlGetPerUserRegistration(bool* pEnabled);
```

### <a name="parameters"></a>Paramètres

*pEnabled*<br/>
[out] TRUE indique que les renseignements sur le registre sont dirigés vers le nœud **HKCU;** FALSE indique que la demande écrit des informations de registre au nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode est efficace, sinon le code d’erreur HRESULT en cas d’erreur se produit.

### <a name="remarks"></a>Notes

La redirection du registre n’est pas activée par défaut. Si vous activez cette option, l’accès au registre est redirigé vers **HKEY_CURRENT_USER -Software-Classes**.

La redirection n’est pas globale. Seuls les cadres MFC et ATL sont affectés par cette réorientation du registre.

### <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="afxregcreatekey"></a><a name="afxregcreatekey"></a>AfxRegCreateKey

Crée la clé de registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegCreateKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey (en)*<br/>
Une poignée à une clé de registre ouvert.

*lpSubKey*<br/>
Le nom d’une clé que cette fonction ouvre ou crée.

*phkResult*<br/>
Un pointeur à une variable qui reçoit une poignée à la clé ouverte ou créée.

*Ptm*<br/>
Pointeur `CAtlTransactionManager` vers un objet.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxregdeletekey"></a><a name="afxregdeletekey"></a>AfxRegDeleteKey AfxRegDeleteKey AfxRegDeleteKey Afx

Supprime la clé de registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegDeleteKey(HKEY hKey, LPCTSTR lpSubKey, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey (en)*<br/>
Une poignée à une clé de registre ouvert.

*lpSubKey*<br/>
Le nom de la clé à supprimer.

*Ptm*<br/>
Pointeur `CAtlTransactionManager` vers un objet.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxregisterpreviewhandler"></a>

Un assistant pour enregistrer un gestionnaire de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxRegisterPreviewHandler(LPCTSTR lpszCLSID, LPCTSTR lpszShortTypeName, LPCTSTR lpszFilterExt);
```

### <a name="parameters"></a>Paramètres

*lpszCLSID (en)*<br/>
Spécifie le CLSID du gestionnaire.

*lpszShortTypeName*<br/>
Spécifie le ProgID du gestionnaire.

*lpszFilterExt*<br/>
Spécifie l’extension de fichier enregistrée auprès de ce gestionnaire.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="atlregistertypelib"></a><a name="atlregistertypelib"></a>AtlRegisterTypeLib

Cette fonction est appelée pour inscrire une bibliothèque de types.

```
ATLAPI AtlRegisterTypeLib(HINSTANCE hInstTypeLib, LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Paramètres

*hInstTypeLib*<br/>
Le manche à l’instance du module.

*lpszIndex*<br/>
Chaîne dans le\\format " N ", où N est l’index integer de la ressource de bibliothèque de type. Peut être NULL si aucun indice n’est requis.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction d’aide est utilisée par [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver) et [CAtlComModule::RegisterTypeLib](../../atl/reference/catlcommodule-class.md#registertypelib).

### <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="afxregopenkey"></a><a name="afxregopenkey"></a>AfxRegOpenKey

Ouvre la clé de registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKey(HKEY hKey, LPCTSTR lpSubKey, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey (en)*<br/>
Une poignée à une clé de registre ouvert.

*lpSubKey*<br/>
Le nom d’une clé que cette fonction ouvre ou crée.

*phkResult*<br/>
Un pointeur à une variable qui reçoit une poignée à la clé créée.

*Ptm*<br/>
Pointeur `CAtlTransactionManager` vers un objet.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxregopenkeyex"></a><a name="afxregopenkeyex"></a>AfxRegOpenKeyEx

Ouvre la clé de registre spécifiée.

### <a name="syntax"></a>Syntaxe

```
LONG AFXAPI AfxRegOpenKeyEx(HKEY hKey, LPCTSTR lpSubKey, DWORD ulOptions, REGSAM samDesired, PHKEY phkResult, CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Paramètres

*hKey (en)*<br/>
Une poignée à une clé de registre ouvert.

*lpSubKey*<br/>
Le nom d’une clé que cette fonction ouvre ou crée.

*ulOptions*<br/>
Ce paramètre est réservé et doit être nul.

*samDesired*<br/>
Un masque qui spécifie les droits d’accès souhaités à la clé.

*phkResult*<br/>
Un pointeur à une variable qui reçoit une poignée à la clé ouverte.

*Ptm*<br/>
Pointeur `CAtlTransactionManager` vers un objet.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit, la valeur de rendement est ERROR_SUCCESS. Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans Winerror.h.

### <a name="requirements"></a>Spécifications

**En-tête :** afxpriv.h

## <a name="afxunregisterpreviewhandler"></a><a name="afxunregisterpreviewhandler"></a>AfxUnregisterPreviewHandler

Un aide pour déenregistrer un gestionnaire de prévisualisation.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxUnRegisterPreviewHandler(LPCTSTR lpszCLSID);
```

### <a name="parameters"></a>Paramètres

*lpszCLSID (en)*<br/>
Spécifie le CLSID du gestionnaire à ne pas être enregistré.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="atlsetperuserregistration"></a><a name="atlsetperuserregistration"></a>AtlSetPerUserRegistration

Définit si l’application redirige l’accès au registre vers le **nœud HKEY_CURRENT_USER** (**HKCU).**

### <a name="syntax"></a>Syntaxe

```
ATLINLINE ATLAPI AtlSetPerUserRegistration(bool bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] TRUE indique que les renseignements sur le registre sont dirigés vers le nœud **HKCU;** FALSE indique que la demande écrit des informations de registre au nœud par défaut. Le nœud par défaut est **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="return-value"></a>Valeur de retour

S_OK si la méthode est efficace, sinon le code d’erreur HRESULT en cas d’erreur se produit.

### <a name="remarks"></a>Notes

La redirection du registre n’est pas activée par défaut. Si vous activez cette option, l’accès au registre est redirigé vers **HKEY_CURRENT_USER -Software-Classes**.

La redirection n’est pas globale. Seuls les cadres MFC et ATL sont affectés par cette réorientation du registre.

### <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlunregistertypelib"></a><a name="atlunregistertypelib"></a>AtlUnRegisterTypeLib

Cette fonction est appelée pour annuler l'inscription d'une bibliothèque de types.

### <a name="syntax"></a>Syntaxe

```
ATLAPI AtlUnRegisterTypeLib(
    HINSTANCE hInstTypeLib,
    LPCOLESTR lpszIndex);
```

### <a name="parameters"></a>Paramètres

*hInstTypeLib*<br/>
Le manche à l’instance du module.

*lpszIndex*<br/>
Chaîne dans le\\format " N ", où N est l’index integer de la ressource de bibliothèque de type. Peut être NULL si aucun indice n’est requis.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction d’aide est utilisée par [CAtlComModule::UnRegisterTypeLib](../../atl/reference/catlcommodule-class.md#unregistertypelib) et [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

### <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="atlloadtypelib"></a><a name="atlloadtypelib"></a>AtlLoadTypeLib

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
Poignée au module associé à la bibliothèque de type.

*lpszIndex*<br/>
Chaîne dans le\\format " N ", où N est l’index integer de la ressource de bibliothèque de type. Peut être NULL si aucun indice n’est requis.

*pbstrPath (en)*<br/>
Au retour réussi, contient le chemin complet du module associé à la bibliothèque de type.

*ppTypeLib*<br/>
Au retour réussi, contient un pointeur à un pointeur à la bibliothèque de type chargé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction d’aide est utilisée par [AtlRegisterTypeLib](#atlregistertypelib) et [AtlUnRegisterTypeLib](#atlunregistertypelib).

## <a name="atlupdateregistryfromresourced"></a><a name="atlupdateregistryfromresourced"></a>AtlUpdateRegistryDeresourceD

Cette fonction a été déconseillée dans Visual Studio 2013 et supprimée dans Visual Studio 2015.

```
<removed>
```

## <a name="registrydataexchange"></a><a name="registrydataexchange"></a>RegistreDataExchange

Cette fonction est appelée pour lire ou écrire dans le Registre système.

### <a name="syntax"></a>Syntaxe

```
HRESULT RegistryDataExchange(
    T* pT,
    enum RDXOperations rdxOp,
    void* pItem = NULL);
```

### <a name="parameters"></a>Paramètres

*Pt*<br/>
Un pointeur vers l’objet actuel.

*rdxOp (en)*<br/>
Une valeur enum qui indique l’opération que la fonction doit effectuer. Voir le tableau dans la section Remarques pour les valeurs autorisées.

*pItem (en)*<br/>
Pointeur vers les données qui doivent être lues à partir du registre ou écrites. Les données peuvent également représenter une clé à supprimer du registre. La valeur par défaut est NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK sur le succès, ou une erreur HRESULT sur l’échec.

### <a name="remarks"></a>Notes

Les macros [BEGIN_RDX_MAP](registry-data-exchange-macros.md#begin_rdx_map) et [END_RDX_MAP](registry-data-exchange-macros.md#end_rdx_map) s’étendre à une `RegistryDataExchange`fonction qui appelle .

Les valeurs enum possibles qui indiquent l’opération que la fonction doit effectuer sont indiquées dans le tableau suivant :

|Valeur Enum|Opération|
|----------------|---------------|
|eReadDeReg|Lisez les données du registre.|
|eWriteToReg|Écrivez des données au registre.|
|eDeleteFromReg|Supprimer la clé du registre.|

### <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="see-also"></a>Voir aussi

[Fonctions](atl-functions.md)<br/>
[Macros d’échange de données de registre](registry-data-exchange-macros.md)

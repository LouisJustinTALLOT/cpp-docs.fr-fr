---
title: CRegKey, classe
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: 3faf446f74577034a3d0676b90ebe7027ef6da06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496533"
---
# <a name="cregkey-class"></a>CRegKey, classe

Cette classe fournit des méthodes pour manipuler des entrées dans le registre système.

> [!IMPORTANT]
>  Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRegKey
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Constructeur.|
|[CRegKey:: ~ CRegKey](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRegKey:: Attach](#attach)|Appelez cette méthode pour attacher un HKEY à l' `CRegKey` objet en affectant à `hKey`la handle de membre [m_hKey](#m_hkey) la valeur.|
|[CRegKey:: Close](#close)|Appelez cette méthode pour libérer le handle de membre [m_hKey](#m_hkey) et lui affecter la valeur null.|
|[CRegKey::Create](#create)|Appelez cette méthode pour créer la clé spécifiée, si elle n’existe pas en tant que sous `hKeyParent`-clé de.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Appelez cette méthode pour supprimer la clé spécifiée du Registre.|
|[CRegKey::DeleteValue](#deletevalue)|Appelez cette méthode pour supprimer un champ de valeur de [m_hKey](#m_hkey).|
|[CRegKey::D Etach](#detach)|Appelez cette méthode pour détacher le handle de membre `CRegKey` [m_hKey](#m_hkey) de l' `m_hKey` objet et lui affecter la valeur null.|
|[CRegKey:: EnumKey](#enumkey)|Appelez cette méthode pour énumérer les sous-clés de la clé de Registre ouverte.|
|[CRegKey:: Flush](#flush)|Appelez cette méthode pour écrire tous les attributs de la clé de Registre Open dans le registre.|
|[CRegKey:: GetKeySecurity](#getkeysecurity)|Appelez cette méthode pour récupérer une copie du descripteur de sécurité protégeant la clé de Registre ouverte.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Cette méthode notifie l’appelant des modifications apportées aux attributs ou au contenu de la clé de Registre ouverte.|
|[CRegKey:: Open](#open)|Appelez cette méthode pour ouvrir la clé spécifiée et définir [m_hKey](#m_hkey) sur le handle de cette clé.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Appelez cette méthode pour récupérer les données binaires pour un nom de valeur spécifié.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Appelez cette méthode pour récupérer les données DWORD pour un nom de valeur spécifié.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Appelez cette méthode pour récupérer les données GUID d’un nom de valeur spécifié.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Appelez cette méthode pour récupérer les données multichaînes pour un nom de valeur spécifié.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Appelez cette méthode pour récupérer les données QWORD pour un nom de valeur spécifié.|
|[CRegKey::QueryStringValue](#querystringvalue)|Appelez cette méthode pour récupérer les données de chaîne d’un nom de valeur spécifié.|
|[CRegKey::QueryValue](#queryvalue)|Appelez cette méthode pour récupérer les données du champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées en tant que ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Appelez cette méthode pour supprimer la clé spécifiée du Registre et supprimer explicitement toutes les sous-clés.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Appelez cette méthode pour définir la valeur binaire de la clé de registre.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Appelez cette méthode pour définir la valeur DWORD de la clé de registre.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Appelez cette méthode pour définir la valeur GUID de la clé de registre.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Appelez cette méthode pour définir la sécurité de la clé de registre.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Appelez cette méthode pour stocker des données dans un champ de valeur spécifié d’une clé spécifiée.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Appelez cette méthode pour définir la valeur multichaîne de la clé de registre.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Appelez cette méthode pour définir la valeur QWORD de la clé de registre.|
|[CRegKey::SetStringValue](#setstringvalue)|Appelez cette méthode pour définir la valeur de chaîne de la clé de registre.|
|[CRegKey::SetValue](#setvalue)|Appelez cette méthode pour stocker des données dans le champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées en tant que ATL_DEPRECATED.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRegKey:: Operator HKEY](#operator_hkey)|Convertit `CRegKey` un objet en HKEY.|
|[CRegKey:: Operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Contient un handle de la clé de registre associée à `CRegKey` l’objet.|
|[CRegKey::m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` un objet|

## <a name="remarks"></a>Notes

`CRegKey`fournit des méthodes pour créer et supprimer des clés et des valeurs dans le registre système. Le registre contient un ensemble de définitions spécifiques à l’installation des composants système, tels que les numéros de version de logiciel, les mappages logiques physique du matériel installé et les objets COM.

`CRegKey`fournit une interface de programmation au registre système pour un ordinateur donné. Par exemple, pour ouvrir une clé de Registre particulière, `CRegKey::Open`appelez. Pour récupérer ou modifier une valeur de données, `CRegKey::QueryValue` appelez `CRegKey::SetValue`ou, respectivement. Pour fermer une clé, appelez `CRegKey::Close`.

Lorsque vous fermez une clé, ses données de Registre sont écrites (vidées) sur le disque dur. Ce processus peut prendre plusieurs secondes. Si votre application doit écrire explicitement des données de Registre sur le disque dur, vous pouvez appeler la fonction Win32 [regflushkey a](/windows/win32/api/winreg/nf-winreg-regflushkey) . Toutefois, `RegFlushKey` utilise de nombreuses ressources système et doit être appelé uniquement lorsque cela est absolument nécessaire.

> [!IMPORTANT]
>  Toutes les méthodes qui permettent à l’appelant de spécifier un emplacement du Registre ont la possibilité de lire des données qui ne peuvent pas être approuvées. Les méthodes qui utilisent [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) doivent tenir compte du fait que cette fonction ne gère pas explicitement les chaînes qui se terminent par une valeur null. Les deux conditions doivent être vérifiées par le code appelant.

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="attach"></a>  CRegKey::Attach

Appelez cette méthode pour attacher un HKEY à l' `CRegKey` objet en affectant à la handle de membre [m_hKey](#m_hkey) la valeur *HKEY*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Paramètres

*hKey*<br/>
Handle d’une clé de registre.

### <a name="remarks"></a>Notes

`Attach`déclare si `m_hKey` est non null.

##  <a name="close"></a>  CRegKey::Close

Appelez cette méthode pour libérer le handle de membre [m_hKey](#m_hkey) et lui affecter la valeur null.

```
LONG Close() throw();
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS; Sinon, retourne une valeur d’erreur.

##  <a name="create"></a>  CRegKey::Create

Appelez cette méthode pour créer la clé spécifiée, si elle n’existe pas en tant que sous-clé de *hKeyParent*.

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*hKeyParent*<br/>
Handle d’une clé ouverte.

*lpszKeyName*<br/>
Spécifie le nom d’une clé à créer ou ouvrir. Ce nom doit être une sous-clé de *hKeyParent*.

*lpszClass*<br/>
Spécifie la classe de la clé à créer ou ouvrir. La valeur par défaut est REG_NONE.

*dwOptions*<br/>
Options de la clé. La valeur par défaut est REG_OPTION_NON_VOLATILE. Pour obtenir la liste des valeurs possibles et des descriptions, consultez [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) dans le SDK Windows.

*samDesired*<br/>
Accès de sécurité pour la clé. La valeur par défaut est &#124; KEY_READ KEY_WRITE. Pour obtenir la liste des valeurs possibles et des descriptions `RegCreateKeyEx`, consultez.

*lpSecAttr*<br/>
Pointeur vers une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui indique si le handle de la clé peut être hérité par un processus enfant. Par défaut, ce paramètre a la valeur NULL (ce qui signifie que le handle ne peut pas être hérité).

*lpdwDisposition*<br/>
à Si la valeur est non NULL, récupère REG_CREATED_NEW_KEY (si la clé n’existait pas et a été créée) ou REG_OPENED_EXISTING_KEY (si la clé existait et a été ouverte).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS et ouvre la clé. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

`Create`définit le membre [m_hKey](#m_hkey) sur le handle de cette clé.

##  <a name="cregkey"></a>  CRegKey::CRegKey

Constructeur.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Référence à un objet `CRegKey`.

*hKey*<br/>
Handle d’une clé de registre.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Crée un objet `CRegKey`. L’objet peut être créé à partir d' `CRegKey` un objet existant ou d’un handle à une clé de registre.

##  <a name="dtor"></a>CRegKey:: ~ CRegKey

Destructeur.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Notes

Le destructeur est libéré `m_hKey`.

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

Appelez cette méthode pour supprimer la clé spécifiée du Registre.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Paramètres

*lpszSubKey*<br/>
Spécifie le nom de la clé à supprimer. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

`DeleteSubKey`peut uniquement supprimer une clé qui n’a pas de sous-clés. Si la clé a des sous-clés, appelez [RecurseDeleteKey](#recursedeletekey) à la place.

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

Appelez cette méthode pour supprimer un champ de valeur de [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Paramètres

*lpszValue*<br/>
Spécifie le champ de valeur à supprimer.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

##  <a name="detach"></a>  CRegKey::Detach

Appelez cette méthode pour détacher le handle de membre `CRegKey` [m_hKey](#m_hkey) de l' `m_hKey` objet et lui affecter la valeur null.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

HKEY associé à l' `CRegKey` objet.

##  <a name="enumkey"></a>  CRegKey::EnumKey

Appelez cette méthode pour énumérer les sous-clés de la clé de Registre ouverte.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*iIndex*<br/>
Index de la sous-clé. Ce paramètre doit être égal à zéro pour le premier appel, puis incrémenté pour les appels suivants

*pszName*<br/>
Pointeur vers une mémoire tampon qui reçoit le nom de la sous-clé, y compris le caractère null de fin. Seul le nom de la sous-clé est copié dans la mémoire tampon, et non dans la hiérarchie de clé complète.

*pnNameLength*<br/>
Pointeur vers une variable qui spécifie la taille, en TCHARs, de la mémoire tampon spécifiée par le paramètre *pszName* . Cette taille doit inclure le caractère null de fin. Lorsque la méthode retourne, la variable vers laquelle pointe *pnNameLength* contient le nombre de caractères stockés dans la mémoire tampon. Le nombre retourné n’inclut pas le caractère null de fin.

*pftLastWriteTime*<br/>
Pointeur vers une variable qui reçoit l’heure de la dernière écriture dans la sous-clé énumérée.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Pour énumérer les sous-clés, `CRegKey::EnumKey` appelez avec un index de zéro. Incrémentez la valeur d’index et répétez l’opération jusqu’à ce que la méthode retourne ERROR_NO_MORE_ITEMS. Pour plus d’informations, consultez [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) dans le SDK Windows.

##  <a name="flush"></a>CRegKey:: Flush

Appelez cette méthode pour écrire tous les attributs de la clé de Registre Open dans le registre.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) dans le SDK Windows.

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

Appelez cette méthode pour récupérer une copie du descripteur de sécurité protégeant la clé de Registre ouverte.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
Valeur [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) qui indique les informations de sécurité demandées.

*psd*<br/>
Pointeur vers une mémoire tampon qui reçoit une copie du descripteur de sécurité demandé.

*pnBytes*<br/>
Taille, en octets, de la mémoire tampon désignée par *PSD*.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro est défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>  CRegKey::m_hKey

Contient un handle de la clé de registre associée à `CRegKey` l’objet.

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

Pointeur vers un `CAtlTransactionManager` objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue

Cette méthode notifie l’appelant des modifications apportées aux attributs ou au contenu de la clé de Registre ouverte.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bWatchSubtree*<br/>
Spécifie un indicateur qui indique s’il faut signaler les modifications dans la clé spécifiée et toutes ses sous-clés ou uniquement dans la clé spécifiée. Si ce paramètre a la valeur TRUE, la méthode signale les modifications apportées à la clé et à ses sous-clés. Si le paramètre a la valeur FALSe, la méthode signale uniquement les modifications dans la clé.

*dwNotifyFilter*<br/>
Spécifie un jeu d’indicateurs qui contrôlent les modifications qui doivent être signalées. Ce paramètre peut être une combinaison des valeurs suivantes:

|`Value`|Signification|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Notifier l’appelant si une sous-clé est ajoutée ou supprimée.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Notifiez l’appelant des modifications apportées aux attributs de la clé, tels que les informations de descripteur de sécurité.|
|REG_NOTIFY_CHANGE_LAST_SET|Notifie l’appelant des modifications apportées à une valeur de la clé. Cela peut inclure l’ajout ou la suppression d’une valeur, ou la modification d’une valeur existante.|
|REG_NOTIFY_CHANGE_SECURITY|Notifie l’appelant des modifications apportées au descripteur de sécurité de la clé.|

*hEvent*<br/>
Handle vers un événement. Si le paramètre *bAsync* a la valeur true, la méthode est retournée immédiatement et les modifications sont signalées en signalant cet événement. Si *bAsync* a la valeur false, *hEvent* est ignoré.

*bAsync*<br/>
Spécifie un indicateur qui indique comment la méthode signale les modifications. Si ce paramètre a la valeur TRUE, la méthode retourne immédiatement et signale les modifications en signalant l’événement spécifié. Lorsque ce paramètre a la valeur FALSe, la méthode n’est pas retournée tant qu’une modification n’a pas eu lieu. Si *hEvent* ne spécifie pas d’événement valide, le paramètre *bAsync* ne peut pas avoir la valeur true.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Cette méthode ne notifie pas l’appelant si la clé spécifiée est supprimée.

Pour plus d’informations et pour obtenir un exemple de programme, consultez [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>CRegKey:: Open

Appelez cette méthode pour ouvrir la clé spécifiée et définir [m_hKey](#m_hkey) sur le handle de cette clé.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Paramètres

*hKeyParent*<br/>
Handle d’une clé ouverte.

*lpszKeyName*<br/>
Spécifie le nom d’une clé à créer ou ouvrir. Ce nom doit être une sous-clé de *hKeyParent*.

*samDesired*<br/>
Accès de sécurité pour la clé. La valeur par défaut est KEY_ALL_ACCESS. Pour obtenir la liste des valeurs possibles et des descriptions, consultez [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS; Sinon, valeur d’erreur différente de zéro définie dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Si le paramètre *lpszKeyName* est null ou pointe vers une chaîne vide, `Open` ouvre un nouveau handle de la clé identifiée par *hKeyParent*, mais ne ferme pas les descripteurs précédemment ouverts.

Contrairement à [CRegKey:: Create](#create), `Open` ne crée pas la clé spécifiée si elle n’existe pas.

##  <a name="operator_hkey"></a>CRegKey:: Operator HKEY

Convertit `CRegKey` un objet en HKEY.

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: Operator =

Opérateur d'assignation.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
Clé à copier.

### <a name="return-value"></a>Valeur de retour

Retourne une référence à la nouvelle clé.

### <a name="remarks"></a>Notes

Cet opérateur détache la *clé* de son objet actuel et l’assigne à l' `CRegKey` objet à la place.

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

Appelez cette méthode pour récupérer les données binaires pour un nom de valeur spécifié.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger.

*pValue*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de la valeur.

*pnBytes*<br/>
Pointeur vers une variable qui spécifie la taille, en octets, de la mémoire tampon vers laquelle pointe le paramètre *pValue* . Lorsque la méthode retourne une valeur, cette variable contient la taille des données copiées dans la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, ERROR_SUCCESS est retourné. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. Manutention. Si les données référencées ne sont pas de type REG_BINARY, ERROR_INVALID_DATA est retourné.

### <a name="remarks"></a>Notes

Cette méthode `RegQueryValueEx` utilise et confirme que le type de données correct est retourné. Pour plus d’informations, consultez [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui se terminent par null. Les deux conditions doivent être vérifiées par le code appelant.

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

Appelez cette méthode pour récupérer les données DWORD pour un nom de valeur spécifié.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger.

*dwValue*<br/>
Pointeur vers une mémoire tampon qui reçoit la valeur DWORD.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, ERROR_SUCCESS est retourné. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. Manutention. Si les données référencées ne sont pas de type REG_DWORD, ERROR_INVALID_DATA est retourné.

### <a name="remarks"></a>Notes

Cette méthode `RegQueryValueEx` utilise et confirme que le type de données correct est retourné. Pour plus d’informations, consultez [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui se terminent par null. Les deux conditions doivent être vérifiées par le code appelant.

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

Appelez cette méthode pour récupérer les données GUID d’un nom de valeur spécifié.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger.

*guidValue*<br/>
Pointeur vers une variable qui reçoit le GUID.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, ERROR_SUCCESS est retourné. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. Manutention. Si les données référencées ne sont pas un GUID valide, ERROR_INVALID_DATA est retourné.

### <a name="remarks"></a>Notes

Cette méthode utilise et convertit la chaîne en GUID à l’aide de `CRegKey::QueryStringValue` [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées.

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

Appelez cette méthode pour récupérer les données multichaînes pour un nom de valeur spécifié.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger.

*pszValue*<br/>
Pointeur vers une mémoire tampon qui reçoit les données multichaînes. Une chaîne multichaîne est un tableau de chaînes terminées par le caractère null, se terminant par deux caractères null.

*pnChars*<br/>
Taille, en TCHARs, de la mémoire tampon vers laquelle pointe *pszValue*. Lorsque la méthode retourne, *pnChars* contient la taille, en TCHARs, de la multichaîne Récupérée, y compris un caractère null de fin.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, ERROR_SUCCESS est retourné. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. Manutention. Si les données référencées ne sont pas de type REG_MULTI_SZ, ERROR_INVALID_DATA est retourné.

### <a name="remarks"></a>Notes

Cette méthode `RegQueryValueEx` utilise et confirme que le type de données correct est retourné. Pour plus d’informations, consultez [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui se terminent par null. Les deux conditions doivent être vérifiées par le code appelant.

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

Appelez cette méthode pour récupérer les données QWORD pour un nom de valeur spécifié.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger.

*qwValue*<br/>
Pointeur vers une mémoire tampon qui reçoit le QWORD.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, ERROR_SUCCESS est retourné. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. Manutention. Si les données référencées ne sont pas de type REG_QWORD, ERROR_INVALID_DATA est retourné.

### <a name="remarks"></a>Notes

Cette méthode `RegQueryValueEx` utilise et confirme que le type de données correct est retourné. Pour plus d’informations, consultez [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui se terminent par null. Les deux conditions doivent être vérifiées par le code appelant.

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

Appelez cette méthode pour récupérer les données de chaîne d’un nom de valeur spécifié.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger.

*pszValue*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de chaîne.

*pnChars*<br/>
Taille, en TCHARs, de la mémoire tampon vers laquelle pointe *pszValue*. Lorsque la méthode retourne, *pnChars* contient la taille, en TCHARs, de la chaîne Récupérée, y compris un caractère null de fin.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, ERROR_SUCCESS est retourné. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. Manutention. Si les données référencées ne sont pas de type REG_SZ, ERROR_INVALID_DATA est retourné. Si la méthode retourne ERROR_MORE_DATA, *pnChars* est égal à zéro, et non à la taille de mémoire tampon requise en octets.

### <a name="remarks"></a>Notes

Cette méthode `RegQueryValueEx` utilise et confirme que le type de données correct est retourné. Pour plus d’informations, consultez [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) .

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui se terminent par null. Les deux conditions doivent être vérifiées par le code appelant.

##  <a name="queryvalue"></a>  CRegKey::QueryValue

Appelez cette méthode pour récupérer les données du champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées en tant que ATL_DEPRECATED.

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à interroger. Si *pszValueName* a la valeur null ou est une chaîne vide, "", la méthode récupère le type et les données pour la valeur sans nom ou par défaut de la clé, le cas échéant.

*pdwType*<br/>
Pointeur vers une variable qui reçoit un code indiquant le type de données stockées dans la valeur spécifiée. Le paramètre *pdwType* peut avoir la valeur null si le code de type n’est pas requis.

*pData*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de la valeur. Ce paramètre peut avoir la valeur NULL si les données ne sont pas requises.

*pnBytes*<br/>
Pointeur vers une variable qui spécifie la taille, en octets, de la mémoire tampon vers laquelle pointe le paramètre *pData* . Lorsque la méthode retourne une valeur, cette variable contient la taille des données copiées dans *pData.*

*dwValue*<br/>
Données numériques du champ de valeur.

*lpszValueName*<br/>
Spécifie le champ de valeur à interroger.

*szValue*<br/>
Données de chaîne du champ de valeur.

*pdwCount*<br/>
Taille des données de chaîne. Sa valeur est initialement définie sur la taille de la mémoire tampon *szValue* .

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS; dans le cas contraire, il s’agit d’un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Les deux versions d’origine `QueryValue` de ne sont plus prises en charge et sont marquées en tant que ATL_DEPRECATED. Le compilateur émet un avertissement si ces formulaires sont utilisés.

La méthode restante appelle RegQueryValueEx.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement du Registre, en lisant potentiellement les données qui ne peuvent pas être approuvées. En outre, la fonction RegQueryValueEx utilisée par cette méthode ne gère pas explicitement les chaînes qui se terminent par NULL. Les deux conditions doivent être vérifiées par le code appelant.

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

Appelez cette méthode pour supprimer la clé spécifiée du Registre et supprimer explicitement toutes les sous-clés.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Paramètres

*lpszKey*<br/>
Spécifie le nom de la clé à supprimer. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS; Sinon, valeur d’erreur différente de zéro définie dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Si la clé a des sous-clés, vous devez appeler cette méthode pour supprimer la clé.

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

Appelez cette méthode pour définir la valeur binaire de la clé de registre.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pValue*<br/>
Pointeur vers une mémoire tampon qui contient les données à stocker avec le nom de valeur spécifié.

*nBytes*<br/>
Spécifie la taille, en octets, des informations vers lesquelles pointe le paramètre *pValue* .

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur dans le registre.

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

Appelez cette méthode pour définir la valeur DWORD de la clé de registre.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*dwValue*<br/>
Données DWORD à stocker avec le nom de valeur spécifié.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur dans le registre.

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

Appelez cette méthode pour définir la valeur GUID de la clé de registre.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*guidValue*<br/>
Référence au GUID à stocker avec le nom de valeur spécifié.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Cette méthode utilise et convertit le GUID en chaîne à l’aide de `CRegKey::SetStringValue` [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

Appelez cette méthode pour stocker des données dans un champ de valeur spécifié d’une clé spécifiée.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszKeyName*<br/>
Spécifie le nom de la clé à créer ou ouvrir. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

*lpszValue*<br/>
Spécifie les données à stocker. Ce paramètre doit être non NULL.

*lpszValueName*<br/>
Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS; dans le cas contraire, il s’agit d’un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Appelez cette méthode pour créer ou ouvrir la clé *lpszKeyName* et stocker les données *lpszValue* dans le champ de valeur *lpszValueName* .

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

Appelez cette méthode pour définir la sécurité de la clé de registre.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
Spécifie les composants du descripteur de sécurité à définir. La valeur peut être une combinaison des valeurs suivantes:

|`Value`|Signification|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Définit la liste de contrôle d’accès discrétionnaire (DACL) de la clé. La clé doit avoir un accès WRITE_DAC, ou le processus appelant doit être le propriétaire de l’objet.|
|GROUP_SECURITY_INFORMATION|Définit l’identificateur de sécurité (SID) du groupe principal de la clé. La clé doit avoir un accès WRITE_OWNER, ou le processus appelant doit être le propriétaire de l’objet.|
|OWNER_SECURITY_INFORMATION|Définit le SID du propriétaire de la clé. La clé doit avoir un accès WRITE_OWNER, ou le processus appelant doit être le propriétaire de l’objet ou disposer du privilège SE_TAKE_OWNERSHIP_NAME activé.|
|SACL_SECURITY_INFORMATION|Définit la liste de contrôle d’accès système (SACL) de la clé. La clé doit avoir un accès ACCESS_SYSTEM_SECURITY. La méthode appropriée pour obtenir cet accès consiste à activer le [privilège](/windows/win32/secauthz/privileges) SE_SECURITY_NAME dans le jeton d’accès actuel de l’appelant, à ouvrir le handle pour l’accès ACCESS_SYSTEM_SECURITY, puis à désactiver le privilège.|

*psd*<br/>
Pointeur vers une structure [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) qui spécifie les attributs de sécurité à définir pour la clé spécifiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Définit les attributs de sécurité de la clé. Pour plus d’informations, consultez [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) .

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

Appelez cette méthode pour définir la valeur multichaîne de la clé de registre.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pszValue*<br/>
Pointeur vers les données multichaînes à stocker avec le nom de valeur spécifié. Une chaîne multichaîne est un tableau de chaînes terminées par le caractère null, se terminant par deux caractères null.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur dans le registre.

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

Appelez cette méthode pour définir la valeur QWORD de la clé de registre.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*qwValue*<br/>
Données QWORD à stocker avec le nom de valeur spécifié.

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur dans le registre.

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

Appelez cette méthode pour définir la valeur de chaîne de la clé de registre.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pszValue*<br/>
Pointeur vers les données de chaîne à stocker avec le nom de valeur spécifié.

*dwType*<br/>
Type de la chaîne à écrire dans le registre: REG_SZ (valeur par défaut) ou REG_EXPAND_SZ (pour les chaînes multichaînes).

### <a name="return-value"></a>Valeur de retour

Si la méthode est réussie, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur dans le registre.

##  <a name="setvalue"></a>  CRegKey::SetValue

Appelez cette méthode pour stocker des données dans le champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées en tant que ATL_DEPRECATED.

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente dans la clé, la méthode l’ajoute à la clé. Si *pszValueName* a la valeur null ou est une chaîne vide, "", la méthode définit le type et les données pour la valeur sans nom ou par défaut de la clé.

*dwType*<br/>
Spécifie un code qui indique le type de données vers lequel pointe le paramètre *pValue* .

*pValue*<br/>
Pointeur vers une mémoire tampon qui contient les données à stocker avec le nom de valeur spécifié.

*nBytes*<br/>
Spécifie la taille, en octets, des informations vers lesquelles pointe le paramètre *pValue* . Si les données sont de type REG_SZ, REG_EXPAND_SZ ou REG_MULTI_SZ, *nBytes* doit inclure la taille du caractère null de fin.

*hKeyParent*<br/>
Handle d’une clé ouverte.

*lpszKeyName*<br/>
Spécifie le nom d’une clé à créer ou ouvrir. Ce nom doit être une sous-clé de *hKeyParent*.

*lpszValue*<br/>
Spécifie les données à stocker. Ce paramètre doit être non NULL.

*lpszValueName*<br/>
Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

*dwValue*<br/>
Spécifie les données à stocker.

*bMulti*<br/>
Si la valeur est false, indique que la chaîne est de type REG_SZ. Si la valeur est true, indique que la chaîne est une chaîne multichaîne de type REG_MULTI_SZ.

*nValueLen*<br/>
Si *bMulti* a la valeur true, *nValueLen* est la longueur de la chaîne *lpszValue* en caractères. Si *bMulti* a la valeur false, la valeur-1 indique que la méthode calculera automatiquement la longueur.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS; dans le cas contraire, il s’agit d’un code d’erreur différent de zéro défini dans WINERROR. Manutention.

### <a name="remarks"></a>Notes

Les deux versions d’origine `SetValue` de sont marquées comme ATL_DEPRECATED et ne doivent plus être utilisées. Le compilateur émet un avertissement si ces formulaires sont utilisés.

La troisième méthode appelle [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Voir aussi

[Exemple DCOM](../../overview/visual-cpp-samples.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

---
title: CRegKey, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a502cbf61f3542c010a89b82131a95f94856cda
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042882"
---
# <a name="cregkey-class"></a>CRegKey, classe

Cette classe fournit des méthodes pour manipuler des entrées dans le Registre système.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRegKey
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Constructeur.|
|[CRegKey :: ~ CRegKey](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRegKey::Attach](#attach)|Appelez cette méthode pour attacher une clé HKEY à la `CRegKey` objet en définissant le [m_hKey](#m_hkey) handle membre vers `hKey`.|
|[CRegKey::Close](#close)|Appelez cette méthode pour libérer le [m_hKey](#m_hkey) membre gérer et affectez-lui la valeur NULL.|
|[CRegKey::Create](#create)|Appelez cette méthode pour créer la clé spécifiée, si elle n’existe pas une sous-clé de `hKeyParent`.|
|[CRegKey::DeleteSubKey](#deletesubkey)|Appelez cette méthode pour supprimer la clé spécifiée à partir du Registre.|
|[CRegKey::DeleteValue](#deletevalue)|Appelez cette méthode pour supprimer un champ de valeur à partir de [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Appelez cette méthode pour détacher le [m_hKey](#m_hkey) handle de membre à partir la `CRegKey` de l’objet et définissez `m_hKey` avec la valeur NULL.|
|[CRegKey::EnumKey](#enumkey)|Appelez cette méthode pour énumérer les sous-clés de la clé de Registre ouverte.|
|[CRegKey::Flush](#flush)|Appelez cette méthode pour écrire tous les attributs de la clé de Registre ouverte dans le Registre.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Appelez cette méthode pour récupérer une copie du descripteur de sécurité qui protège la clé de Registre ouverte.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Cette méthode notifie l’appelant sur les modifications apportées au contenu de la clé de Registre ouverte ou attributs.|
|[CRegKey::Open](#open)|Appelez cette méthode pour ouvrir la clé spécifiée et définir [m_hKey](#m_hkey) au handle de cette clé.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Appelez cette méthode pour récupérer les données binaires pour un nom de la valeur spécifiée.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Appelez cette méthode pour récupérer les données de la valeur DWORD pour un nom de la valeur spécifiée.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Appelez cette méthode pour récupérer les données GUID pour un nom de la valeur spécifiée.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Appelez cette méthode pour récupérer les données de chaîne multiple pour un nom de la valeur spécifiée.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Appelez cette méthode pour récupérer les données QWORD pour un nom de la valeur spécifiée.|
|[CRegKey::QueryStringValue](#querystringvalue)|Appelez cette méthode pour récupérer les données de chaîne pour un nom de la valeur spécifiée.|
|[CRegKey::QueryValue](#queryvalue)|Appelez cette méthode pour récupérer les données pour le champ de valeur spécifié [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Appelez cette méthode pour supprimer la clé spécifiée à partir du Registre et supprimer toutes les sous-clés de manière explicite.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Appelez cette méthode pour définir la valeur binaire de la clé de Registre.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Appelez cette méthode pour définir la valeur DWORD de la clé de Registre.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Appelez cette méthode pour définir la valeur GUID de la clé de Registre.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Appelez cette méthode pour définir la sécurité de la clé de Registre.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Appelez cette méthode pour stocker des données dans un champ de valeur spécifiée d’une clé spécifiée.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Appelez cette méthode pour définir la valeur de chaîne multiple de la clé de Registre.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Appelez cette méthode pour définir la valeur QWORD la clé de Registre.|
|[CRegKey::SetStringValue](#setstringvalue)|Appelez cette méthode pour définir la valeur de chaîne de la clé de Registre.|
|[CRegKey::SetValue](#setvalue)|Appelez cette méthode pour stocker des données dans le champ de valeur spécifié [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::operator HKEY](#operator_hkey)|Convertit un `CRegKey` objet à un HKEY.|
|[CRegKey::operator =](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Contient un handle de la clé de Registre associé à la `CRegKey` objet.|
|[CRegKey::m_pTM](#m_ptm)|Pointeur vers `CAtlTransactionManager` objet|

## <a name="remarks"></a>Notes

`CRegKey` Fournit des méthodes pour créer et supprimer des clés et valeurs dans le Registre système. Le Registre contient un ensemble spécifique de l’installation des définitions pour les composants système, tels que les numéros de version des logiciels, les mappages physiques logiques de matériel installé et des objets COM.

`CRegKey` Fournit une interface de programmation dans le Registre système pour un ordinateur donné. Par exemple, pour ouvrir une clé de Registre spécifiques, appelez `CRegKey::Open`. Pour récupérer ou modifier une valeur de données, appelez `CRegKey::QueryValue` ou `CRegKey::SetValue`, respectivement. Pour fermer une clé, appelez `CRegKey::Close`.

Lorsque vous fermez une clé, ses données de Registre sont écrit (vidées) sur le disque dur. Ce processus peut prendre plusieurs secondes. Si votre application doit écrire explicitement des données de Registre sur le disque dur, vous pouvez appeler la [RegFlushKey](/windows/desktop/api/winreg/nf-winreg-regflushkey) fonction Win32. Toutefois, `RegFlushKey` utilise beaucoup de ressources système et doit être appelé uniquement lorsque cela est absolument nécessaire.

> [!IMPORTANT]
>  Les méthodes qui permettent à l’appelant de spécifier un emplacement de Registre ont la possibilité de lire les données qui ne peut pas être approuvées. Utilisent des méthodes qui permettent de [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) à prendre en compte cette fonction ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="attach"></a>  CRegKey::Attach

Appelez cette méthode pour attacher une clé HKEY à la `CRegKey` objet en définissant le [m_hKey](#m_hkey) handle membre vers *hKey*.

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Paramètres

*clé hKey*<br/>
Le handle d’une clé de Registre.

### <a name="remarks"></a>Notes

`Attach` vérifie si `m_hKey` n’est pas NULL.

##  <a name="close"></a>  CRegKey::Close

Appelez cette méthode pour libérer le [m_hKey](#m_hkey) membre gérer et affectez-lui la valeur NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS ; Sinon, retourne une valeur d’erreur.

##  <a name="create"></a>  CRegKey::Create

Appelez cette méthode pour créer la clé spécifiée, si elle n’existe pas une sous-clé de *hKeyParent*.

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
Le handle d’une clé ouverte.

*lpszKeyName*<br/>
Spécifie le nom d’une clé pour être créé ou ouvert. Ce nom doit être une sous-clé de *hKeyParent*.

*lpszClass*<br/>
Spécifie la classe de la clé à être créé ou ouvert. La valeur par défaut est REG_NONE.

*dwOptions*<br/>
Options de la clé. La valeur par défaut est REG_OPTION_NON_VOLATILE. Pour obtenir la liste de valeurs possibles et les descriptions, consultez [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) dans le SDK Windows.

*samDesired*<br/>
L’accès de sécurité pour la clé. La valeur par défaut est KEY_READ &#124; KEY_WRITE. Pour obtenir la liste de valeurs possibles et les descriptions, consultez `RegCreateKeyEx`.

*lpSecAttr*<br/>
Un pointeur vers un [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) structure qui indique si le handle de la clé peut être hérité par un processus enfant. Par défaut, ce paramètre est NULL (c'est-à-dire le handle ne peut pas être hérité).

*lpdwDisposition*<br/>
[out] Si non NULL, récupère REG_CREATED_NEW_KEY (si la clé n’existait pas et a été créée) ou REG_OPENED_EXISTING_KEY (si la clé existait et a été ouvert).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS et ouvre la clé. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

`Create` définit le [m_hKey](#m_hkey) membre vers le handle de cette clé.

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

*clé hKey*<br/>
Handle vers une clé de Registre.

*pTM*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Crée un objet `CRegKey`. L’objet peut être créé à partir d’un existant `CRegKey` objet, ou à partir d’un handle vers une clé de Registre.

##  <a name="dtor"></a>  CRegKey :: ~ CRegKey

Destructeur.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Notes

Les versions de destructeur `m_hKey`.

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

Appelez cette méthode pour supprimer la clé spécifiée à partir du Registre.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Paramètres

*lpszSubKey*<br/>
Spécifie le nom de la clé à supprimer. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

`DeleteSubKey` peut supprimer uniquement une clé qui ne possède des sous-clés aucun. Si la clé possède des sous-clés, appelez [RecurseDeleteKey](#recursedeletekey) à la place.

##  <a name="deletevalue"></a>  CRegKey::DeleteValue

Appelez cette méthode pour supprimer un champ de valeur à partir de [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Paramètres

*lpszValue*<br/>
Spécifie le champ de valeur à supprimer.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

##  <a name="detach"></a>  CRegKey::Detach

Appelez cette méthode pour détacher le [m_hKey](#m_hkey) handle de membre à partir la `CRegKey` de l’objet et définissez `m_hKey` avec la valeur NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Clé HKEY associé le `CRegKey` objet.

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
L’index de sous-clés. Ce paramètre doit être zéro pour le premier appel et ensuite incrémentée pour les appels suivants

*pszName*<br/>
Pointeur vers une mémoire tampon qui reçoit le nom de la sous-clé, y compris le caractère null de fin. Uniquement le nom de la sous-clé est copié vers la mémoire tampon, et non la hiérarchie de clés complète.

*pnNameLength*<br/>
Pointeur vers une variable qui spécifie la taille, en TCHARs, de la mémoire tampon spécifiée par le *pszName* paramètre. Cette taille doit inclure le caractère null de fin. Lorsque la méthode est retournée, la variable vers laquelle pointe *pnNameLength* contient le nombre de caractères stockés dans la mémoire tampon. Le nombre retourné n’inclut pas le caractère null de fin.

*pftLastWriteTime*<br/>
Pointeur vers une variable qui reçoit l’heure la sous-clé énumérée la dernière écriture dans.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Pour énumérer les sous-clés, appelez `CRegKey::EnumKey` avec un index de zéro. Incrémenter la valeur d’index et répétez jusqu'à ce que la méthode retourne ERROR_NO_MORE_ITEMS. Pour plus d’informations, consultez [RegEnumKeyEx](/windows/desktop/api/winreg/nf-winreg-regenumkeyexa) dans le SDK Windows.

##  <a name="flush"></a>  CRegKey::Flush

Appelez cette méthode pour écrire tous les attributs de la clé de Registre ouverte dans le Registre.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [RegEnumFlush](/windows/desktop/api/winreg/nf-winreg-regflushkey) dans le SDK Windows.

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

Appelez cette méthode pour récupérer une copie du descripteur de sécurité qui protège la clé de Registre ouverte.

```
LONG GetKeySecurity(  
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Paramètres

*Si*<br/>
Le [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) valeur qui indique les informations de sécurité demandé.

*PSD*<br/>
Pointeur vers une mémoire tampon qui reçoit une copie du descripteur de sécurité demandé.

*pnBytes*<br/>
La taille, en octets, de la mémoire tampon vers laquelle pointé *psd*.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est qu'un code d’erreur différent de zéro est défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [RegGetKeySecurity](/windows/desktop/api/winreg/nf-winreg-reggetkeysecurity).

##  <a name="m_hkey"></a>  CRegKey::m_hKey

Contient un handle de la clé de Registre associé à la `CRegKey` objet.

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

Cette méthode notifie l’appelant sur les modifications apportées au contenu de la clé de Registre ouverte ou attributs.

```
LONG NotifyChangeKeyValue(  
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bWatchSubtree*<br/>
Spécifie un indicateur qui indique s’il faut signaler les modifications dans la clé spécifiée et toutes ses sous-clés ou uniquement dans la clé spécifiée. Si ce paramètre est TRUE, la méthode signale les modifications apportées à la clé et ses sous-clés. Si le paramètre est FALSE, la méthode signale les modifications uniquement dans la clé.

*dwNotifyFilter*<br/>
Spécifie un jeu d’indicateurs qui contrôlent les modifications qui doit être signalé. Ce paramètre peut être une combinaison des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Informer l’appelant si une sous-clé est ajoutée ou supprimée.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Informer l’appelant des modifications apportées aux attributs de la clé, telles que les informations de descripteur de sécurité.|
|REG_NOTIFY_CHANGE_LAST_SET|Informer l’appelant des modifications apportées à une valeur de la clé. Cela peut inclure Ajout ou la suppression d’une valeur ou la modification d’une valeur existante.|
|REG_NOTIFY_CHANGE_SECURITY|Informer l’appelant des modifications au descripteur de sécurité de la clé.|

*hEvent*<br/>
Handle vers un événement. Si le *bAsync* paramètre est TRUE, la méthode retourne immédiatement et les modifications sont signalées par la signalisation de cet événement. Si *bAsync* est FALSE, *hEvent* est ignoré.

*bAsync*<br/>
Spécifie un indicateur qui détermine comment la méthode signale les modifications apportées. Si ce paramètre est TRUE, la méthode retourne immédiatement et signale les modifications apportées par la signalisation de l’événement spécifié. Lorsque ce paramètre est FALSE, la méthode ne retourne pas jusqu'à ce qu’une modification a eu lieu. Si *hEvent* ne spécifie pas un événement valide, le *bAsync* paramètre ne peut pas être TRUE.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

> [!NOTE]
>  Cette méthode n’informe pas l’appelant si la clé spécifiée est supprimée.

Pour plus d’informations et un exemple de programme, consultez [RegNotifyChangeKeyValue](/windows/desktop/api/winreg/nf-winreg-regnotifychangekeyvalue).

##  <a name="open"></a>  CRegKey::Open

Appelez cette méthode pour ouvrir la clé spécifiée et définir [m_hKey](#m_hkey) au handle de cette clé.

```
LONG Open(  
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Paramètres

*hKeyParent*<br/>
Le handle d’une clé ouverte.

*lpszKeyName*<br/>
Spécifie le nom d’une clé pour être créé ou ouvert. Ce nom doit être une sous-clé de *hKeyParent*.

*samDesired*<br/>
L’accès de sécurité pour la clé. La valeur par défaut est KEY_ALL_ACCESS. Pour obtenir la liste de valeurs possibles et les descriptions, consultez [RegCreateKeyEx](/windows/desktop/api/winreg/nf-winreg-regcreatekeyexa) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS ; Sinon, une valeur d’erreur différent de zéro est définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Si le *lpszKeyName* paramètre est NULL ou pointe vers une chaîne vide, `Open` ouvre un nouveau descripteur de la clé identifiée par *hKeyParent*, mais ne ferme pas un handle quelconque précédemment ouvert.

Contrairement aux [CRegKey::Create](#create), `Open` ne crée pas la clé spécifiée si elle n’existe pas.

##  <a name="operator_hkey"></a>  CRegKey::operator HKEY

Convertit un `CRegKey` objet à un HKEY.

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>  CRegKey::operator =

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

Cet opérateur détache *clé* à partir de son objet en cours et l’assigne à la `CRegKey` à la place de l’objet.

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

Appelez cette méthode pour récupérer les données binaires pour un nom de la valeur spécifiée.

```
LONG QueryBinaryValue(  
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête.

*pValue*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de la valeur.

*pnBytes*<br/>
Pointeur vers une variable qui spécifie la taille, en octets, de la mémoire tampon vers laquelle pointe le *pValue* paramètre. Lorsque la méthode est retournée, cette variable contient la taille des données copiées vers la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est renvoyé. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_BINARY, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type de données correct est retourné. Consultez [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) pour plus d’informations.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées. En outre, le [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) fonction utilisée par cette méthode ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

Appelez cette méthode pour récupérer les données de la valeur DWORD pour un nom de la valeur spécifiée.

```
LONG QueryDWORDValue(  
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête.

*dwValue*<br/>
Pointeur vers une mémoire tampon qui reçoit la valeur DWORD.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est renvoyé. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_DWORD, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type de données correct est retourné. Consultez [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) pour plus d’informations.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées. En outre, le [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) fonction utilisée par cette méthode ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

Appelez cette méthode pour récupérer les données GUID pour un nom de la valeur spécifiée.

```
LONG QueryGUIDValue(  
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête.

*guidValue*<br/>
Pointeur vers une variable qui reçoit le GUID.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est renvoyé. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. H. Si les données référencées ne sont pas un GUID valide, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `CRegKey::QueryStringValue` et convertit la chaîne en un GUID à l’aide [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées.

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

Appelez cette méthode pour récupérer les données de chaîne multiple pour un nom de la valeur spécifiée.

```
LONG QueryMultiStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête.

*pszValue*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de chaîne multiple. Une chaîne multiple est un tableau de chaînes terminées par deux caractères null.

*pnChars*<br/>
La taille, en TCHARs, de la mémoire tampon vers laquelle pointé *pszValue*. Lorsque la méthode est retournée, *pnChars* contient la taille, en TCHARs, de multi-chaîne récupéré, y compris un caractère null de fin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est renvoyé. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_MULTI_SZ, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type de données correct est retourné. Consultez [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) pour plus d’informations.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées. En outre, le [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) fonction utilisée par cette méthode ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

Appelez cette méthode pour récupérer les données QWORD pour un nom de la valeur spécifiée.

```
LONG QueryQWORDValue(  
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête.

*qwValue*<br/>
Pointeur vers une mémoire tampon qui reçoit le QWORD.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est renvoyé. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_QWORD, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type de données correct est retourné. Consultez [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) pour plus d’informations.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées. En outre, le [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) fonction utilisée par cette méthode ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

Appelez cette méthode pour récupérer les données de chaîne pour un nom de la valeur spécifiée.

```
LONG QueryStringValue(  
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête.

*pszValue*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de chaîne.

*pnChars*<br/>
La taille, en TCHARs, de la mémoire tampon vers laquelle pointé *pszValue*. Lorsque la méthode est retournée, *pnChars* contient la taille, en TCHARs, de la chaîne extraite, y compris un caractère null de fin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est renvoyé. Si la méthode ne parvient pas à lire une valeur, elle retourne un code d’erreur différent de zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_SZ, ERROR_INVALID_DATA est retournée. Si la méthode retourne ERROR_MORE_DATA, *pnChars* est égal à zéro, pas la taille de mémoire tampon requise en octets.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type de données correct est retourné. Consultez [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) pour plus d’informations.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées. En outre, le [RegQueryValueEx](/windows/desktop/api/winreg/nf-winreg-regqueryvalueexa) fonction utilisée par cette méthode ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

##  <a name="queryvalue"></a>  CRegKey::QueryValue

Appelez cette méthode pour récupérer les données pour le champ de valeur spécifié [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.

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
Pointeur vers une chaîne se terminant par null qui contient le nom de la valeur de la requête. Si *pszValueName* est NULL ou une chaîne vide, « », la méthode récupère le type et les données de la clé du sans nom ou valeur par défaut, si un.

*pdwType*<br/>
Pointeur vers une variable qui reçoit un code indiquant le type de données stockées dans la valeur spécifiée. Le *pdwType* paramètre peut être NULL si le code de type n’est pas obligatoire.

*pData*<br/>
Pointeur vers une mémoire tampon qui reçoit les données de la valeur. Ce paramètre peut être NULL si les données ne sont pas requises.

*pnBytes*<br/>
Pointeur vers une variable qui spécifie la taille, en octets, de la mémoire tampon vers laquelle pointe le *pData* paramètre. Lorsque la méthode est retournée, cette variable contient la taille des copie des données *pData.*

*dwValue*<br/>
Données numériques du champ de valeur.

*lpszValueName*<br/>
Spécifie le champ de valeur à interroger.

*szValue*<br/>
Données de chaîne du champ de valeur.

*pdwCount*<br/>
La taille de la chaîne. Sa valeur est initialement définie sur la taille de la *szValue* mémoire tampon.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS ; Sinon, un code d’erreur différent de zéro est définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Les deux versions d’origine de `QueryValue` ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED. Le compilateur émet un avertissement si ces formes sont utilisées.

Les appels de méthode restants RegQueryValueEx.

> [!IMPORTANT]
>  Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de Registre, lecture potentiellement des données qui ne peut pas être approuvées. En outre, la fonction RegQueryValueEx utilisée par cette méthode ne gère pas explicitement les chaînes qui ont la valeur NULL s’est arrêté. Les deux conditions de doivent être vérifiées par le code appelant.

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

Appelez cette méthode pour supprimer la clé spécifiée à partir du Registre et supprimer toutes les sous-clés de manière explicite.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Paramètres

*lpszKey*<br/>
Spécifie le nom de la clé à supprimer. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS ; Sinon, une valeur d’erreur différent de zéro est définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Si la clé possède des sous-clés, vous devez appeler cette méthode pour supprimer la clé.

##  <a name="setbinaryvalue"></a>  CRegKey::SetBinaryValue

Appelez cette méthode pour définir la valeur binaire de la clé de Registre.

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
Pointeur vers une mémoire tampon contenant les données doit être stockée avec le nom de la valeur spécifiée.

*nBytes*<br/>
Spécifie la taille, en octets, des informations vers lequel pointé le *pValue* paramètre.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pour écrire la valeur dans le Registre.

##  <a name="setdwordvalue"></a>  CRegKey::SetDWORDValue

Appelez cette méthode pour définir la valeur DWORD de la clé de Registre.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*dwValue*<br/>
Les données DWORD doit être stockée avec le nom de la valeur spécifiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pour écrire la valeur dans le Registre.

##  <a name="setguidvalue"></a>  CRegKey::SetGUIDValue

Appelez cette méthode pour définir la valeur GUID de la clé de Registre.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*guidValue*<br/>
Référence vers le GUID doit être stockée avec le nom de la valeur spécifiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise `CRegKey::SetStringValue` et convertit les GUID en une chaîne à l’aide [StringFromGUID2](/windows/desktop/api/combaseapi/nf-combaseapi-stringfromguid2).

##  <a name="setkeyvalue"></a>  CRegKey::SetKeyValue

Appelez cette méthode pour stocker des données dans un champ de valeur spécifiée d’une clé spécifiée.

```
LONG SetKeyValue(  
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszKeyName*<br/>
Spécifie le nom de la clé à être créé ou ouvert. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

*lpszValue*<br/>
Spécifie les données à stocker. Ce paramètre doit être non NULL.

*lpszValueName*<br/>
Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS ; Sinon, un code d’erreur différent de zéro est définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Appelez cette méthode pour créer ou ouvrir le *lpszKeyName* de clé et de stocker le *lpszValue* données dans le *lpszValueName* champ de valeur.

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

Appelez cette méthode pour définir la sécurité de la clé de Registre.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Paramètres

*Si*<br/>
Spécifie les composants du descripteur de sécurité à définir. La valeur peut être une combinaison des valeurs suivantes :

|Value|Signification|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Définit la liste de contrôle d’accès discrétionnaire de la clé (DACL). La clé doit avoir l’accès WRITE_DAC, ou le processus appelant doit être propriétaire de l’objet.|
|GROUP_SECURITY_INFORMATION|Définit l’identificateur de sécurité de groupe principal de la clé (SID). La clé doit avoir l’accès WRITE_OWNER, ou le processus appelant doit être propriétaire de l’objet.|
|OWNER_SECURITY_INFORMATION|Définit le SID du propriétaire de la clé. La clé doit avoir l’accès WRITE_OWNER, ou le processus appelant doit être propriétaire de l’objet ou avoir le privilège SE_TAKE_OWNERSHIP_NAME activé.|
|SACL_SECURITY_INFORMATION|Définit la liste de contrôle d’accès de la clé système (SACL). La clé doit avoir accès aux ACCESS_SYSTEM_SECURITY. La méthode appropriée pour obtenir cet accès consiste à activer le SE_SECURITY_NAME [privilège](https://msdn.microsoft.com/library/windows/desktop/aa379306) dans le jeton d’accès actuel de l’appelant, ouvrir un handle pour un accès ACCESS_SYSTEM_SECURITY et désactivez le privilège.|

*PSD*<br/>
Pointeur vers un [SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor) structure qui spécifie les attributs de sécurité à définir pour la clé spécifiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Définit les attributs de sécurité de la clé. Consultez [RegSetKeySecurity](/windows/desktop/api/winreg/nf-winreg-regsetkeysecurity) pour plus d’informations.

##  <a name="setmultistringvalue"></a>  CRegKey::SetMultiStringValue

Appelez cette méthode pour définir la valeur de chaîne multiple de la clé de Registre.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pszValue*<br/>
Pointeur vers les données de chaîne multiple doit être stockée avec le nom de la valeur spécifiée. Une chaîne multiple est un tableau de chaînes terminées par deux caractères null.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pour écrire la valeur dans le Registre.

##  <a name="setqwordvalue"></a>  CRegKey::SetQWORDValue

Appelez cette méthode pour définir la valeur QWORD la clé de Registre.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*qwValue*<br/>
Les données QWORD doit être stockée avec le nom de la valeur spécifiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pour écrire la valeur dans le Registre.

##  <a name="setstringvalue"></a>  CRegKey::SetStringValue

Appelez cette méthode pour définir la valeur de chaîne de la clé de Registre.

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
Pointeur vers les données de chaîne doit être stockée avec le nom de la valeur spécifiée.

*dwType*<br/>
Le type de la chaîne à écrire dans le Registre : REG_SZ (la valeur par défaut) ou REG_EXPAND_SZ (pour les multistrings).

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de retour est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur différent de zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa) pour écrire la valeur dans le Registre.

##  <a name="setvalue"></a>  CRegKey::SetValue

Appelez cette méthode pour stocker des données dans le champ de valeur spécifié [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.

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
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur portant ce nom n’est pas déjà présente dans la clé, la méthode l’ajoute à la clé. Si *pszValueName* est NULL ou une chaîne vide, « », la méthode définit le type et les données de la clé du sans nom ou valeur par défaut.

*dwType*<br/>
Spécifie un code indiquant le type de données vers lequel pointés le *pValue* paramètre.

*pValue*<br/>
Pointeur vers une mémoire tampon contenant les données doit être stockée avec le nom de la valeur spécifiée.

*nBytes*<br/>
Spécifie la taille, en octets, des informations vers lequel pointé le *pValue* paramètre. Si les données sont de type REG_SZ, REG_EXPAND_SZ ou REG_MULTI_SZ, *nBytes* doit inclure la taille du caractère null de fin.

*hKeyParent*<br/>
Le handle d’une clé ouverte.

*lpszKeyName*<br/>
Spécifie le nom d’une clé pour être créé ou ouvert. Ce nom doit être une sous-clé de *hKeyParent*.

*lpszValue*<br/>
Spécifie les données à stocker. Ce paramètre doit être non NULL.

*lpszValueName*<br/>
Spécifie le champ de valeur à définir. Si un champ de valeur portant ce nom n’existe pas déjà dans la clé, il est ajouté.

*dwValue*<br/>
Spécifie les données à stocker.

*bMulti*<br/>
Si la valeur est false, indique la chaîne est de type REG_SZ. Si la valeur est true, indique que la chaîne est une multiple de longueur fixe de type REG_MULTI_SZ.

*nValueLen*<br/>
Si *bMulti* a la valeur true, *nValueLen* est la longueur de la *lpszValue* chaîne en caractères. Si *bMulti* a la valeur false, la valeur -1 indique que la méthode calcule automatiquement la longueur.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne ERROR_SUCCESS ; Sinon, un code d’erreur différent de zéro est définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Les deux versions d’origine de `SetValue` sont marqués comme ATL_DEPRECATED et ne doit plus être utilisé. Le compilateur émet un avertissement si ces formes sont utilisées.

La troisième méthode appelle [RegSetValueEx](/windows/desktop/api/winreg/nf-winreg-regsetvalueexa).

## <a name="see-also"></a>Voir aussi

[Exemple DCOM](../../visual-cpp-samples.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)

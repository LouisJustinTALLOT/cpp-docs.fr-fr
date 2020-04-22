---
title: Classe CRegKey
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
ms.openlocfilehash: d3bdb2e7c3ab0ef56ef7f6fba5d43f1ba0bb7fc6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746508"
---
# <a name="cregkey-class"></a>Classe CRegKey

Cette classe fournit des méthodes pour manipuler les entrées dans le registre du système.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CRegKey
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|Constructeur.|
|[CRegKey: : CRegKey](#dtor)|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRegKey::Attach](#attach)|Appelez cette méthode pour attacher `CRegKey` un HKEY à l’objet `hKey`en définissant la poignée [m_hKey](#m_hkey) membre à .|
|[CRegKey::Fermer](#close)|Appelez cette méthode pour libérer la [poignée m_hKey](#m_hkey) membre et la définir à NULL.|
|[CRegKey::Créer](#create)|Appelez cette méthode pour créer la clé spécifiée, si `hKeyParent`elle n’existe pas comme une sous-clé de .|
|[CRegKey::DeleteSubKey](#deletesubkey)|Appelez cette méthode pour supprimer la clé spécifiée du registre.|
|[CRegKey::DeleteValue](#deletevalue)|Appelez cette méthode pour supprimer un champ de valeur de [m_hKey](#m_hkey).|
|[CRegKey::Detach](#detach)|Appelez cette méthode pour détacher la [poignée](#m_hkey) `CRegKey` m_hKey membre `m_hKey` de l’objet et réglée à NULL.|
|[CRegKey::EnumKey](#enumkey)|Appelez cette méthode pour énumérer les sous-clés de la clé de registre ouvert.|
|[CRegKey::Flush](#flush)|Appelez cette méthode pour écrire tous les attributs de la clé de registre ouvert dans le registre.|
|[CRegKey::GetKeySecurity](#getkeysecurity)|Appelez cette méthode pour récupérer une copie du descripteur de sécurité protégeant la clé de registre ouvert.|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|Cette méthode informe l’appelant des modifications apportées aux attributs ou au contenu de la clé de registre ouvert.|
|[CRegKey::Ouvert](#open)|Appelez cette méthode pour ouvrir la clé spécifiée et définir [m_hKey](#m_hkey) à la poignée de cette clé.|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|Appelez cette méthode pour récupérer les données binaires pour un nom de valeur spécifié.|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|Appelez cette méthode pour récupérer les données DWORD pour un nom de valeur spécifié.|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|Appelez cette méthode pour récupérer les données GUID pour un nom de valeur spécifié.|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|Appelez cette méthode pour récupérer les données multicordes pour un nom de valeur spécifié.|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|Appelez cette méthode pour récupérer les données QWORD pour un nom de valeur spécifié.|
|[CRegKey::QueryStringValue](#querystringvalue)|Appelez cette méthode pour récupérer les données de chaîne pour un nom de valeur spécifié.|
|[CRegKey::QueryValue](#queryvalue)|Appelez cette méthode pour récupérer les données pour le champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|Appelez cette méthode pour supprimer la clé spécifiée du registre et supprimer explicitement les sous-clés.|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|Appelez cette méthode pour définir la valeur binaire de la clé de registre.|
|[CRegKey::SetDWORDValue](#setdwordvalue)|Appelez cette méthode pour définir la valeur DWORD de la clé de registre.|
|[CRegKey::SetGUIDValue](#setguidvalue)|Appelez cette méthode pour définir la valeur GUID de la clé de registre.|
|[CRegKey::SetKeySecurity](#setkeysecurity)|Appelez cette méthode pour définir la sécurité de la clé de registre.|
|[CRegKey::SetKeyValue](#setkeyvalue)|Appelez cette méthode pour stocker des données dans un champ de valeur spécifié d’une clé spécifiée.|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|Appelez cette méthode pour définir la valeur multicorde de la clé de registre.|
|[CRegKey::SetQWORDValue](#setqwordvalue)|Appelez cette méthode pour définir la valeur QWORD de la clé de registre.|
|[CRegKey::SetStringValue](#setstringvalue)|Appelez cette méthode pour définir la valeur de chaîne de la clé de registre.|
|[CRegKey::SetValue](#setvalue)|Appelez cette méthode pour stocker des données dans le champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::opérateur HKEY](#operator_hkey)|Convertit `CRegKey` un objet en HKEY.|
|[CRegKey::opérateur](#operator_eq)|Opérateur d'assignation.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|Contient une poignée de la `CRegKey` clé de registre associée à l’objet.|
|[CRegKey::m_pTM](#m_ptm)|Pointeur `CAtlTransactionManager` à objecter|

## <a name="remarks"></a>Notes

`CRegKey`fournit des méthodes pour créer et supprimer les clés et les valeurs dans le registre du système. Le registre contient un ensemble spécifique à l’installation de définitions pour les composants du système, tels que les numéros de version logicielle, les cartographies logiques à physiques du matériel installé et les objets COM.

`CRegKey`fournit une interface de programmation au registre du système pour une machine donnée. Par exemple, pour ouvrir une `CRegKey::Open`clé de registre particulière, appelez . Pour récupérer ou modifier une `CRegKey::QueryValue` `CRegKey::SetValue`valeur de données, appelez ou, respectivement. Pour fermer une `CRegKey::Close`clé, appelez .

Lorsque vous fermez une clé, ses données de registre sont écrites (flushed) sur le disque dur. Ce processus peut prendre plusieurs secondes. Si votre application doit écrire explicitement des données de registre sur le disque dur, vous pouvez appeler la fonction [RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32. Cependant, `RegFlushKey` utilise de nombreuses ressources système et ne doit être appelé que lorsque cela est absolument nécessaire.

> [!IMPORTANT]
> Toutes les méthodes qui permettent à l’appelant de spécifier un emplacement de registre ont le potentiel de lire des données qui ne peuvent pas faire confiance. Les méthodes qui utilisent [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) doivent tenir compte du fait que cette fonction ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="cregkeyattach"></a><a name="attach"></a>CRegKey::Attach

Appelez cette méthode pour attacher `CRegKey` un HKEY à l’objet en définissant la [poignée m_hKey](#m_hkey) membre à *hKey*.

```cpp
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>Paramètres

*hKey (en)*<br/>
Le manche d’une clé de registre.

### <a name="remarks"></a>Notes

`Attach`s’il `m_hKey` n’est pas NULL.

## <a name="cregkeyclose"></a><a name="close"></a>CRegKey::Fermer

Appelez cette méthode pour libérer la [poignée m_hKey](#m_hkey) membre et la définir à NULL.

```
LONG Close() throw();
```

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS; retourne autrement une valeur d’erreur.

## <a name="cregkeycreate"></a><a name="create"></a>CRegKey::Créer

Appelez cette méthode pour créer la clé spécifiée, si elle n’existe pas comme une sous-clé de *hKeyParent*.

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

*hKeyParent (en)*<br/>
Le manche d’une clé ouverte.

*lpszKeyName (en)*<br/>
Spécifie le nom d’une clé à créer ou à ouvrir. Ce nom doit être une sous-clé de *hKeyParent*.

*Classe lpsz*<br/>
Spécifie la classe de la clé à créer ou à ouvrir. La valeur par défaut est REG_NONE.

*dwOptions*<br/>
Options pour la clé. La valeur par défaut est REG_OPTION_NON_VOLATILE. Pour une liste de valeurs et de descriptions possibles, voir [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) dans le SDK Windows.

*samDesired*<br/>
L’accès à la sécurité pour la clé. La valeur par défaut est KEY_READ &#124; KEY_WRITE. Pour une liste de valeurs et `RegCreateKeyEx`de descriptions possibles, voir .

*lpSecAttr*<br/>
Un pointeur d’une structure [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) qui indique si la poignée de la clé peut être héritée par un processus d’enfant. Par défaut, ce paramètre est NULL (ce qui signifie que la poignée ne peut pas être héritée).

*lpdwDisposition*<br/>
[out] En cas de non-NULL, récupère soit REG_CREATED_NEW_KEY (si la clé n’existait pas et a été créée) ou REG_OPENED_EXISTING_KEY (si la clé existait et a été ouverte).

### <a name="return-value"></a>Valeur de retour

En cas de succès, retourne ERROR_SUCCESS et ouvre la clé. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

`Create`définit le [m_hKey](#m_hkey) membre à la poignée de cette clé.

## <a name="cregkeycregkey"></a><a name="cregkey"></a>CRegKey::CRegKey

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

*hKey (en)*<br/>
Une poignée à une clé de registre.

*Ptm*<br/>
Pointeur vers l'objet CAtlTransactionManager

### <a name="remarks"></a>Notes

Crée un objet `CRegKey`. L’objet peut être `CRegKey` créé à partir d’un objet existant, ou d’une poignée à une clé de registre.

## <a name="cregkeycregkey"></a><a name="dtor"></a>CRegKey: : CRegKey

Destructeur.

```
~CRegKey() throw();
```

### <a name="remarks"></a>Notes

Le destructor `m_hKey`libère .

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a>CRegKey::DeleteSubKey

Appelez cette méthode pour supprimer la clé spécifiée du registre.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>Paramètres

*lpszSubKey*<br/>
Spécifie le nom de la clé à supprimer. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

`DeleteSubKey`ne peut supprimer qu’une clé qui n’a pas de sous-clés. Si la clé a des sous-clés, appelez [RecurseDeleteKey](#recursedeletekey) à la place.

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a>CRegKey::DeleteValue

Appelez cette méthode pour supprimer un champ de valeur de [m_hKey](#m_hkey).

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>Paramètres

*lpszValue*<br/>
Spécifie le champ de valeur à supprimer.

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

## <a name="cregkeydetach"></a><a name="detach"></a>CRegKey::Detach

Appelez cette méthode pour détacher la [poignée](#m_hkey) `CRegKey` m_hKey membre `m_hKey` de l’objet et réglée à NULL.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>Valeur de retour

Le HKEY associé `CRegKey` à l’objet.

## <a name="cregkeyenumkey"></a><a name="enumkey"></a>CRegKey::EnumKey

Appelez cette méthode pour énumérer les sous-clés de la clé de registre ouvert.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*iIndex (en)*<br/>
L’indice subkey. Ce paramètre doit être nul pour le premier appel, puis incrémenté pour les appels ultérieurs

*pszName (en)*<br/>
Pointeur vers un tampon qui reçoit le nom du sous-clé, y compris le caractère nul de fin. Seul le nom du sous-clé est copié sur le tampon, et non sur la hiérarchie complète des clés.

*pnNameLength*<br/>
Pointeur vers une variable qui spécifie la taille, dans les TCHAR, du tampon spécifié par le paramètre *pszName.* Cette taille devrait inclure le caractère nul de fin. Lorsque la méthode revient, la variable pointée par *pnNameLength* contient le nombre de caractères stockés dans le tampon. Le compte rendu n’inclut pas le caractère nul de fin.

*pftLastWriteTime pftLastWriteTime*<br/>
Pointeur à une variable qui reçoit le temps que le sous-clé énuméré a été écrit pour la dernière fois.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Pour énumérer les sous-clés, appelez `CRegKey::EnumKey` avec un index de zéro. Incrément de la valeur de l’indice et répéter jusqu’à ce que la méthode retourne ERROR_NO_MORE_ITEMS. Pour plus d’informations, voir [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) dans windows SDK.

## <a name="cregkeyflush"></a><a name="flush"></a>CRegKey::Flush

Appelez cette méthode pour écrire tous les attributs de la clé de registre ouvert dans le registre.

```
LONG Flush() throw();
```

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) dans windows SDK.

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a>CRegKey::GetKeySecurity

Appelez cette méthode pour récupérer une copie du descripteur de sécurité protégeant la clé de registre ouvert.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
La [valeur SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) qui indique les informations de sécurité demandées.

*Psd*<br/>
Un pointeur vers un tampon qui reçoit une copie du descripteur de sécurité demandé.

*pnBytes (pnBytes)*<br/>
La taille, dans les octets, de la mémoire tampon pointée par *psd*.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro est défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity).

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a>CRegKey::m_hKey

Contient une poignée de la `CRegKey` clé de registre associée à l’objet.

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a>CRegKey::m_pTM

Pointeur `CAtlTransactionManager` vers un objet.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Notes

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue

Cette méthode informe l’appelant des modifications apportées aux attributs ou au contenu de la clé de registre ouvert.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>Paramètres

*bWatchSubtree*<br/>
Précise un indicateur qui indique s’il convient de signaler les changements dans la clé spécifiée et tous ses sous-clés ou seulement dans la clé spécifiée. Si ce paramètre est VRAI, la méthode signale des changements dans la clé et ses sous-clés. Si le paramètre est FALSE, les rapports de méthode ne changent que dans la clé.

*dwNotifyFilter*<br/>
Spécifie un ensemble de drapeaux qui contrôlent les changements qui doivent être signalés. Ce paramètre peut être une combinaison des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|Informez l’appelant si un sous-clé est ajouté ou supprimé.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|Avisez l’appelant des modifications aux attributs de la clé, tels que les informations descripteur de sécurité.|
|REG_NOTIFY_CHANGE_LAST_SET|Avisez l’appelant des modifications à une valeur de la clé. Cela peut inclure l’ajout ou la suppression d’une valeur, ou la modification d’une valeur existante.|
|REG_NOTIFY_CHANGE_SECURITY|Avisez l’appelant des modifications apportées au descripteur de sécurité de la clé.|

*hEvent*<br/>
Handle vers un événement. Si le *paramètre bAsync* est VRAI, la méthode revient immédiatement et les modifications sont signalées en signalant cet événement. Si *bAsync* est FALSE, *hEvent* est ignoré.

*bAsync*<br/>
Spécifie un drapeau qui indique comment la méthode signale les changements. Si ce paramètre est VRAI, la méthode revient immédiatement et signale les changements en signalant l’événement spécifié. Lorsque ce paramètre est FALSE, la méthode ne revient pas jusqu’à ce qu’un changement se soit produit. Si *hEvent* ne spécifie pas un événement valide, le paramètre *bAsync* ne peut pas être VRAI.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

> [!NOTE]
> Cette méthode n’avise pas l’appelant si la clé spécifiée est supprimée.

Pour plus de détails et un programme d’exemple, voir [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue).

## <a name="cregkeyopen"></a><a name="open"></a>CRegKey::Ouvert

Appelez cette méthode pour ouvrir la clé spécifiée et définir [m_hKey](#m_hkey) à la poignée de cette clé.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>Paramètres

*hKeyParent (en)*<br/>
Le manche d’une clé ouverte.

*lpszKeyName (en)*<br/>
Spécifie le nom d’une clé à créer ou à ouvrir. Ce nom doit être une sous-clé de *hKeyParent*.

*samDesired*<br/>
L’accès à la sécurité pour la clé. La valeur par défaut est KEY_ALL_ACCESS. Pour une liste de valeurs et de descriptions possibles, voir [RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS; autrement, une valeur d’erreur non nulle définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Si le paramètre *lpszKeyName* est NULL `Open` ou indique une chaîne vide, ouvre une nouvelle poignée de la clé identifiée par *hKeyParent*, mais ne ferme aucune poignée précédemment ouverte.

Contrairement à [CRegKey::Créer](#create), `Open` ne créera pas la clé spécifiée si elle n’existe pas.

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a>CRegKey::opérateur HKEY

Convertit `CRegKey` un objet en HKEY.

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a>CRegKey::opérateur

Opérateur d'assignation.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>Paramètres

*key*<br/>
La clé à copier.

### <a name="return-value"></a>Valeur de retour

Renvoie une référence à la nouvelle clé.

### <a name="remarks"></a>Notes

Cet opérateur détache la *clé* de son objet `CRegKey` actuel et l’attribue plutôt à l’objet.

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue

Appelez cette méthode pour récupérer les données binaires pour un nom de valeur spécifié.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête.

*pValue*<br/>
Pointer vers un tampon qui reçoit les données de la valeur.

*pnBytes (pnBytes)*<br/>
Pointeur vers une variable qui spécifie la taille, dans les octets, du tampon pointé vers le paramètre *pValue.* Lorsque la méthode revient, cette variable contient la taille des données copiées sur le tampon.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est retournée. Si la méthode ne lit pas une valeur, elle renvoie un code d’erreur non zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_BINARY, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type correct de données est retourné. Voir [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) pour plus de détails.

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a>CRegKey::QueryDWORDValue

Appelez cette méthode pour récupérer les données DWORD pour un nom de valeur spécifié.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête.

*dwValue dwValue*<br/>
Pointeur vers un tampon qui reçoit le DWORD.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est retournée. Si la méthode ne lit pas une valeur, elle renvoie un code d’erreur non zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_DWORD, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type correct de données est retourné. Voir [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) pour plus de détails.

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a>CRegKey::QueryGUIDValue

Appelez cette méthode pour récupérer les données GUID pour un nom de valeur spécifié.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête.

*guidValue*<br/>
Pointeur vers une variable qui reçoit le GUID.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est retournée. Si la méthode ne lit pas une valeur, elle renvoie un code d’erreur non zéro défini dans WINERROR. H. Si les données référencées ne sont pas un GUID valide, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `CRegKey::QueryStringValue` et convertit la chaîne en GUID à l’aide [de CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring).

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance.

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue

Appelez cette méthode pour récupérer les données multicordes pour un nom de valeur spécifié.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête.

*pszValue*<br/>
Pointeur vers un tampon qui reçoit les données multicordes. Une multicorde est un tableau de cordes non terminées, terminée par deux caractères nuls.

*pnChars (pnChars)*<br/>
La taille, dans les TCHAR, de la mémoire tampon pointée par *pszValue*. Lorsque la méthode revient, *pnChars* contient la taille, en TCHARs, du multicordage récupéré, y compris un caractère nul mettant fin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est retournée. Si la méthode ne lit pas une valeur, elle renvoie un code d’erreur non zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_MULTI_SZ, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type correct de données est retourné. Voir [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) pour plus de détails.

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

Appelez cette méthode pour récupérer les données QWORD pour un nom de valeur spécifié.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête.

*qwValue*<br/>
Pointeur vers un tampon qui reçoit le QWORD.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est retournée. Si la méthode ne lit pas une valeur, elle renvoie un code d’erreur non zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_QWORD, ERROR_INVALID_DATA est retournée.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type correct de données est retourné. Voir [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) pour plus de détails.

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a>CRegKey::QueryStringValue

Appelez cette méthode pour récupérer les données de chaîne pour un nom de valeur spécifié.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête.

*pszValue*<br/>
Pointeur vers un tampon qui reçoit les données de chaîne.

*pnChars (pnChars)*<br/>
La taille, dans les TCHAR, de la mémoire tampon pointée par *pszValue*. Lorsque la méthode revient, *pnChars* contient la taille, en TCHARs, de la chaîne récupérée, y compris un caractère nul de fin.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, ERROR_SUCCESS est retournée. Si la méthode ne lit pas une valeur, elle renvoie un code d’erreur non zéro défini dans WINERROR. H. Si les données référencées ne sont pas de type REG_SZ, ERROR_INVALID_DATA est retournée. Si la méthode revient ERROR_MORE_DATA, *pnChars* est égal à zéro, et non à la taille du tampon requis dans les octets.

### <a name="remarks"></a>Notes

Cette méthode utilise `RegQueryValueEx` et confirme que le type correct de données est retourné. Voir [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) pour plus de détails.

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance. En outre, la fonction [RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) utilisée par cette méthode ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a>CRegKey::QueryValue

Appelez cette méthode pour récupérer les données pour le champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.

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
Pointeur vers une chaîne désinsavenue contenant le nom de la valeur à la requête. Si *pszValueName* est NULL ou une chaîne vide, ", la méthode récupère le type et les données pour la valeur sans nom ou par défaut de la clé, le cas échéant.

*pdwType*<br/>
Pointeur vers une variable qui reçoit un code indiquant le type de données stockées dans la valeur spécifiée. Le paramètre *pdwType* peut être NULL si le code de type n’est pas nécessaire.

*Pdata*<br/>
Pointer vers un tampon qui reçoit les données de la valeur. Ce paramètre peut être NULL si les données ne sont pas nécessaires.

*pnBytes (pnBytes)*<br/>
Pointeur vers une variable qui spécifie la taille, dans les octets, du tampon pointé vers le paramètre *pData.* Lorsque la méthode revient, cette variable contient la taille des données copiées sur *pData.*

*dwValue dwValue*<br/>
Les données numériques du champ de valeur.

*lpszValueName*<br/>
Spécifie le champ de valeur à interroger.

*szValue (en)*<br/>
Les données de chaîne du champ de valeur.

*pdwCompte*<br/>
La taille des données de chaîne. Sa valeur est initialement réglée à la taille du tampon *szValue.*

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS; autrement, un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Les deux versions `QueryValue` originales de ne sont plus pris en charge et sont marquées comme ATL_DEPRECATED. Le compilateur émettra un avertissement si ces formulaires sont utilisés.

La méthode restante appelle RegQueryValueEx.

> [!IMPORTANT]
> Cette méthode permet à l’appelant de spécifier n’importe quel emplacement de registre, en lisant potentiellement des données qui ne peuvent pas faire confiance. En outre, la fonction RegQueryValueEx utilisée par cette méthode ne gère pas explicitement les chaînes qui sont annulées. Les deux conditions doivent être vérifiées par le code d’appel.

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

Appelez cette méthode pour supprimer la clé spécifiée du registre et supprimer explicitement les sous-clés.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>Paramètres

*lpszKey (en)*<br/>
Spécifie le nom de la clé à supprimer. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS; autrement, une valeur d’erreur non nulle définie dans WINERROR. H.

### <a name="remarks"></a>Notes

Si la clé a des sous-clés, vous devez appeler cette méthode pour supprimer la clé.

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

Appelez cette méthode pour définir la valeur binaire de la clé de registre.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pValue*<br/>
Pointeur vers un tampon contenant les données à stocker avec le nom de valeur spécifié.

*nBytes (en)*<br/>
Spécifie la taille, dans les octets, des informations pointées par le paramètre *pValue.*

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur au registre.

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a>CRegKey::SetDWORDValue

Appelez cette méthode pour définir la valeur DWORD de la clé de registre.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*dwValue dwValue*<br/>
Les données DWORD à stocker avec le nom de valeur spécifié.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur au registre.

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a>CRegKey::SetGUIDValue

Appelez cette méthode pour définir la valeur GUID de la clé de registre.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*guidValue*<br/>
Référence au GUID à stocker avec le nom de valeur spécifié.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise `CRegKey::SetStringValue` et convertit le GUID en une chaîne à l’aide [de StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2).

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a>CRegKey::SetKeyValue

Appelez cette méthode pour stocker des données dans un champ de valeur spécifié d’une clé spécifiée.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszKeyName (en)*<br/>
Précise le nom de la clé à créer ou à ouvrir. Ce nom doit être une sous-clé de [m_hKey](#m_hkey).

*lpszValue*<br/>
Spécifie les données à stocker. Ce paramètre doit être non-NULL.

*lpszValueName*<br/>
Spécifie le champ de valeur à définir. Si un champ de valeur avec ce nom n’existe pas déjà dans la clé, il est ajouté.

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS; autrement, un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Appelez cette méthode pour créer ou ouvrir la clé *lpszKeyName* et stocker les données *lpszValue* dans le champ de valeur *lpszValueName.*

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a>CRegKey::SetKeySecurity

Appelez cette méthode pour définir la sécurité de la clé de registre.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>Paramètres

*si*<br/>
Spécifie les composants du descripteur de sécurité à définir. La valeur peut être une combinaison des valeurs suivantes :

|Valeur|Signification|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|Définit la liste discrétionnaire de contrôle d’accès de la clé (DACL). La clé doit avoir WRITE_DAC accès, ou le processus d’appel doit être le propriétaire de l’objet.|
|GROUP_SECURITY_INFORMATION|Définit l’identifiant de sécurité du groupe principal (SID) de la clé. La clé doit avoir WRITE_OWNER accès, ou le processus d’appel doit être le propriétaire de l’objet.|
|OWNER_SECURITY_INFORMATION|Définit le propriétaire de la clé SID. La clé doit avoir WRITE_OWNER accès, ou le processus d’appel doit être le propriétaire de l’objet ou avoir le privilège SE_TAKE_OWNERSHIP_NAME activé.|
|SACL_SECURITY_INFORMATION|Définit la liste de contrôle d’accès du système (SACL) du système. La clé doit avoir ACCESS_SYSTEM_SECURITY accès. La bonne façon d’obtenir cet accès est de permettre le [privilège](/windows/win32/secauthz/privileges) SE_SECURITY_NAME dans le jeton d’accès actuel de l’appelant, d’ouvrir la poignée pour ACCESS_SYSTEM_SECURITY accès, puis de désactiver le privilège.|

*Psd*<br/>
Pointeur vers une structure [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) qui spécifie les attributs de sécurité à définir pour la clé spécifiée.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Définit les attributs de sécurité de la clé. Voir [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) pour plus de détails.

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue

Appelez cette méthode pour définir la valeur multicorde de la clé de registre.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pszValue*<br/>
Pointeur vers les données multicordes à stocker avec le nom de valeur spécifié. Une multicorde est un tableau de cordes non terminées, terminée par deux caractères nuls.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur au registre.

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a>CRegKey::SetQWORDValue

Appelez cette méthode pour définir la valeur QWORD de la clé de registre.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*qwValue*<br/>
Les données QWORD à stocker avec le nom de valeur spécifié.

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur au registre.

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a>CRegKey::SetStringValue

Appelez cette méthode pour définir la valeur de chaîne de la clé de registre.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>Paramètres

*pszValueName*<br/>
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente, la méthode l’ajoute à la clé.

*pszValue*<br/>
Pointeur vers les données de chaîne à stocker avec le nom de valeur spécifié.

*dwType dwType*<br/>
Le type de la chaîne à écrire au registre : soit REG_SZ (par défaut) soit REG_EXPAND_SZ (pour les cordes multiples).

### <a name="return-value"></a>Valeur de retour

Si la méthode réussit, la valeur de rendement est ERROR_SUCCESS. Si la méthode échoue, la valeur de retour est un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Cette méthode utilise [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) pour écrire la valeur au registre.

## <a name="cregkeysetvalue"></a><a name="setvalue"></a>CRegKey::SetValue

Appelez cette méthode pour stocker des données dans le champ de valeur spécifié de [m_hKey](#m_hkey). Les versions antérieures de cette méthode ne sont plus prises en charge et sont marquées comme ATL_DEPRECATED.

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
Pointeur vers une chaîne contenant le nom de la valeur à définir. Si une valeur avec ce nom n’est pas déjà présente dans la clé, la méthode l’ajoute à la clé. Si *pszValueName* est NULL ou une chaîne vide, "", la méthode définit le type et les données pour la valeur sans nom ou par défaut de la clé.

*dwType dwType*<br/>
Spécifie un code indiquant le type de données indiquées par le paramètre *pValue.*

*pValue*<br/>
Pointeur vers un tampon contenant les données à stocker avec le nom de valeur spécifié.

*nBytes (en)*<br/>
Spécifie la taille, dans les octets, des informations pointées par le paramètre *pValue.* Si les données sont de type REG_SZ, REG_EXPAND_SZ ou REG_MULTI_SZ, *les nBytes* doivent inclure la taille du caractère nul de fin.

*hKeyParent (en)*<br/>
Le manche d’une clé ouverte.

*lpszKeyName (en)*<br/>
Spécifie le nom d’une clé à créer ou à ouvrir. Ce nom doit être une sous-clé de *hKeyParent*.

*lpszValue*<br/>
Spécifie les données à stocker. Ce paramètre doit être non-NULL.

*lpszValueName*<br/>
Spécifie le champ de valeur à définir. Si un champ de valeur avec ce nom n’existe pas déjà dans la clé, il est ajouté.

*dwValue dwValue*<br/>
Spécifie les données à stocker.

*bMulti*<br/>
Si elle est fausse, indique que la chaîne est de type REG_SZ. Si c’est vrai, indique que la ficelle est une multicorde de type REG_MULTI_SZ.

*nValueLen (en)*<br/>
Si *bMulti* est vrai, *nValueLen* est la longueur de la chaîne *lpszValue* en caractères. Si *bMulti* est faux, une valeur de -1 indique que la méthode calculera automatiquement la longueur.

### <a name="return-value"></a>Valeur de retour

En cas de succès, les retours ERROR_SUCCESS; autrement, un code d’erreur non zéro défini dans WINERROR. H.

### <a name="remarks"></a>Notes

Les deux versions `SetValue` originales sont marquées comme ATL_DEPRECATED et ne doivent plus être utilisées. Le compilateur émettra un avertissement si ces formulaires sont utilisés.

La troisième méthode appelle [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw).

## <a name="see-also"></a>Voir aussi

[Échantillon DCOM](../../overview/visual-cpp-samples.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)

---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: b1acf959c371aa23ac55ace7fea9466f0e20813f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318470"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Encapsule les fonctions API Windows, fournissant une interface orientée objet que vous utilisez pour accéder au Registre.

## <a name="syntax"></a>Syntaxe

```
class CSettingsStore : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSettingsStore::CSettingsStore](#csettingsstore)|Construit un objet `CSettingsStore`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSettingsStore::Fermer](#close)|Ferme la clé de registre ouvert.|
|[CSettingsStore::CreateKey](#createkey)|Ouvre la clé spécifiée ou la crée si elle n’existe pas.|
|[CSettingsStore::DeleteKey](#deletekey)|Supprime la clé spécifiée et tous ses enfants.|
|[CSettingsStore::DeleteValue](#deletevalue)|Supprime la valeur spécifiée de la clé ouverte.|
|[CSettingsStore::Ouvert](#open)|Ouvre la clé spécifiée.|
|[CSettingsStore::Lire](#read)|Récupère les données pour une valeur clé spécifiée.|
|[CSettingsStore::Ecrire](#write)|Écrit une valeur au registre sous la clé ouverte.|

## <a name="remarks"></a>Notes

Le membre `CreateKey` fonctionne `Open` et sont très similaires. Si la clé du `CreateKey` registre `Open` existe déjà, et fonctionne de la même manière. Toutefois, si la clé du `CreateKey` registre n’existe pas, la créera alors qu’elle `Open` retournera une valeur d’erreur.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les méthodes `CSettingsStore` Open et Read de la classe. Cet extrait de code fait partie de [l’échantillon de démonstration de bout d’outil.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Spécifications

**En-tête:** afxsettingsstore.h

## <a name="csettingsstoreclose"></a><a name="close"></a>CSettingsStore::Fermer

Ferme la clé de registre ouvert.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode est appelée à partir du destructeur de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a>CSettingsStore::CreateKey

Ouvre une clé de registre ou la crée si elle n’existe pas.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Paramètres

*pszPath (pszPath)*<br/>
[dans] Spécifie le nom d’une clé à créer ou à ouvrir.

### <a name="return-value"></a>Valeur de retour

0 en cas de succès; sinon une valeur non zéro.

### <a name="remarks"></a>Notes

`CreateKey`comme `m_hKey` racine des enquêtes sur le registre. Il recherche *pszPath* comme une `m_hKey`sous-clé de . Si la clé n’existe pas, `CreateKey` la crée. Sinon, il ouvre la clé. `CreateKey`puis `m_hKey` se fixe à la clé créée ou ouverte.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a>CSettingsStore::CSettingsStore

Crée un objet `CSettngsStore` .

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Paramètres

*bAdmin (en)*<br/>
[dans] Paramètre Boolean qui précise `CSettingsStore` si l’objet agit en mode administrateur.

*bReadOnly*<br/>
[dans] Paramètre Boolean qui précise `CSettingsStore` si l’objet est créé en mode lecture uniquement.

### <a name="remarks"></a>Notes

Si *bAdmin* est réglé `m_hKey` sur TRUE, la variable du membre est configuré pour **HKEY_LOCAL_MACHINE**. Si vous définissez *bAdmin* à FALSE, `m_hKey` est réglé pour **HKEY_CURRENT_USER**.

L’accès de sécurité dépend du *paramètre bReadOnly.* Si *bReadonly* est FALSE, l’accès à la sécurité sera mis à **KEY_ALL_ACCESS**. Si *bReadyOnly* est VRAI, l’accès à la sécurité sera fixé à une combinaison de **KEY_QUERY_VALUE, KEY_NOTIFY** et **KEY_ENUMERATE_SUB_KEYS**. Pour plus d’informations sur l’accès à la sécurité ainsi que le registre, voir [Les droits de sécurité et d’accès clés du Registre](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Le destructeur pour `CSettingsStore` `m_hKey` les versions automatiquement.

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a>CSettingsStore::DeleteKey

Supprime une clé et tous ses enfants du registre.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Paramètres

*pszPath (pszPath)*<br/>
[dans] Le nom de la clé à supprimer.

*bAdmin (en)*<br/>
[dans] Commutateur qui spécifie l’emplacement de la clé à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode échouera `CSettingsStore` si l’objet est en mode lecture uniquement.

Si le paramètre *bAdmin* est nul, `DeleteKey` recherche la clé à supprimer sous **HKEY_CURRENT_USER**. Si *bAdmin n’est* paszero, `DeleteKey` recherche la clé à supprimer sous **HKEY_LOCAL_MACHINE**.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a>CSettingsStore::DeleteValue

Supprime une valeur `m_hKey`de .

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Paramètres

*pszValue*<br/>
[dans] Spécifie le champ de valeur à supprimer.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="csettingsstoreopen"></a><a name="open"></a>CSettingsStore::Ouvert

Ouvre une clé de registre.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Paramètres

*pszPath (pszPath)*<br/>
[dans] Le nom d’une clé de registre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Après que cette méthode ouvre avec `m_hKey` succès la clé spécifiée, elle se définit à la poignée de cette clé.

## <a name="csettingsstoreread"></a><a name="read"></a>CSettingsStore::Lire

Lit une valeur à partir d’une clé dans le registre.

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>Paramètres

*pszKey (en)*<br/>
[dans] Pointeur vers une chaîne non terminée qui contient le nom de la valeur à lire à partir du registre.

*iVal (en)*<br/>
[out] Référence à une variable d’intégrant qui reçoit la valeur lue à partir de la clé du registre.

*dwVal (en)*<br/>
[out] Référence à une variable de 32 bits à double mot qui reçoit la valeur lue à partir de la clé du registre.

*sVal (en)*<br/>
[out] Référence à une variable de chaîne qui reçoit la valeur lue à partir de la clé de registre.

*scStringList (en)*<br/>
[out] Référence à une variable de liste de chaînes qui reçoit la valeur lue à partir de la clé du registre.

*scArray scArray*<br/>
[out] Référence à une variable de tableau de chaîne qui reçoit la valeur lue à partir de la clé de registre.

*dwcArray dwcArray*<br/>
[out] Référence à une variable de tableau à deux mots 32 bits qui reçoit la valeur lue à partir de la clé du registre.

*wcArray (en)*<br/>
[out] Référence à une variable de tableau de 16 bits qui reçoit la valeur lue à partir de la clé du registre.

*bcArray (en)*<br/>
[out] Référence à une variable de tableau d’enre-titres qui reçoit la valeur lue à partir de la clé de registre.

*lpPoint (en)*<br/>
[out] Référence à un `POINT` pointeur à une structure qui reçoit la valeur lue à partir de la clé du registre.

*Rect*<br/>
[out] Référence à une variable [CRect](../../atl-mfc-shared/reference/crect-class.md) qui reçoit la valeur lue à partir de la clé du registre.

*ppData (en)*<br/>
[out] Pointeur vers un pointeur vers les données qui reçoit la valeur lue à partir de la clé de registre.

*pBytes (en)*<br/>
[out] Pointeur vers une variable insignable non signée. Cette variable reçoit la taille du tampon que *ppData* pointe vers.

*list*<br/>
[out] Référence à une variable [CObList](../../mfc/reference/coblist-class.md) qui reçoit la valeur lue à partir de la clé de registre.

*obj*<br/>
[out] Référence à une variable [CObject](../../mfc/reference/cobject-class.md) qui reçoit la valeur lue à partir de la clé de registre.

*pObj pObj*<br/>
[out] Référence à un `CObject` pointeur à une variable qui reçoit la valeur lue à partir de la clé du registre.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Read`vérifie pour *pszKey* comme `m_hKey`une sous-clé de .

## <a name="csettingsstorewrite"></a><a name="write"></a>CSettingsStore::Ecrire

Écrit une valeur au registre sous la clé ouverte.

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>Paramètres

*pszKey (en)*<br/>
[dans] Pointeur vers une chaîne qui contient le nom de la valeur à définir.

*iVal (en)*<br/>
[dans] Référence à une variable d’intégrant qui contient les données à stocker.

*dwVal (en)*<br/>
[dans] Référence à une variable de 32 bits à double mot qui contient les données à stocker.

*pszVal (en)*<br/>
[dans] Pointeur vers une variable de chaîne à durée nulle qui contient les données à stocker.

*scStringList (en)*<br/>
[dans] Référence à une variable [CStringList](../../mfc/reference/cstringlist-class.md) qui contient les données à stocker.

*bcArray (en)*<br/>
[dans] Référence à une variable de tableau d’entrée qui contient les données à stocker.

*scArray scArray*<br/>
[dans] Référence à une variable de tableau de chaîne qui contient les données à stocker.

*dwcArray dwcArray*<br/>
[dans] Référence à une variable de tableau à deux mots 32 bits qui contient les données à stocker.

*wcArray (en)*<br/>
[dans] Référence à une variable de tableau de mots 16 bits qui contient les données à stocker.

*Rect*<br/>
[dans] Référence à une variable [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient les données à stocker.

*lpPoint (en)*<br/>
[dans] Référence à un `POINT` pointeur à une variable qui contient les données à stocker.

*Pdata*<br/>
[dans] Pointeur vers un tampon qui contient les données à stocker.

*nBytes (en)*<br/>
[dans] Spécifie la taille, dans les octets, des données auxquelles le paramètre *pData* indique.

*list*<br/>
[dans] Référence à une variable [CObList](../../mfc/reference/coblist-class.md) qui contient les données à stocker.

*obj*<br/>
[dans] Référence à une variable [CObject](../../mfc/reference/cobject-class.md) qui contient les données à stocker.

*pObj pObj*<br/>
[dans] Pointeur vers un `CObject` pointeur à une variable qui contient les données à stocker.

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Afin d’écrire au registre, vous devez définir *bReadOnly* à une valeur non zéro lorsque vous créez un objet [CSettingsStore.](../../mfc/reference/csettingsstore-class.md) Pour plus d’informations, voir [CSettingsStore::CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)

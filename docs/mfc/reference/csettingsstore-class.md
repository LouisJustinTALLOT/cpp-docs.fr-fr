---
description: 'En savoir plus sur : classe CSettingsStore'
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
ms.openlocfilehash: a1e2e52c59c4c7cf6139e1215c901a49095616b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342889"
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
|[CSettingsStore :: CSettingsStore](#csettingsstore)|Construit un objet `CSettingsStore`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSettingsStore :: Close](#close)|Ferme la clé de Registre ouverte.|
|[CSettingsStore :: CreateKey](#createkey)|Ouvre la clé spécifiée ou la crée si elle n’existe pas.|
|[CSettingsStore ::D eleteKey](#deletekey)|Supprime la clé spécifiée et tous ses enfants.|
|[CSettingsStore ::D eleteValue](#deletevalue)|Supprime la valeur spécifiée de la clé ouverte.|
|[CSettingsStore :: Open](#open)|Ouvre la clé spécifiée.|
|[CSettingsStore :: lecture](#read)|Récupère les données pour une valeur de clé spécifiée.|
|[CSettingsStore :: Write](#write)|Écrit une valeur dans le Registre sous la clé ouverte.|

## <a name="remarks"></a>Notes

Les fonctions membres `CreateKey` et `Open` sont très similaires. Si la clé de Registre existe déjà `CreateKey` et `Open` fonctionne de la même façon. Toutefois, si la clé de Registre n’existe pas, la `CreateKey` créera alors qu' `Open` une valeur d’erreur est retournée.

## <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser les méthodes d’ouverture et de lecture de la `CSettingsStore` classe. Cet extrait de code fait partie de l’exemple de démonstration de l' [info-bulle](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>Spécifications

**En-tête :** afxsettingsstore. h

## <a name="csettingsstoreclose"></a><a name="close"></a> CSettingsStore :: Close

Ferme la clé de Registre ouverte.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Par défaut, cette méthode est appelée à partir du destructeur de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a> CSettingsStore :: CreateKey

Ouvre une clé de registre ou la crée si elle n’existe pas.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>Paramètres

*pszPath*<br/>
dans Spécifie le nom d’une clé à créer ou ouvrir.

### <a name="return-value"></a>Valeur renvoyée

0 en cas de réussite ; Sinon, une valeur différente de zéro.

### <a name="remarks"></a>Notes

`CreateKey` utilise `m_hKey` comme racine des recherches dans le registre. Il recherche *pszPath* en tant que sous-clé de `m_hKey` . Si la clé n’existe pas, la `CreateKey` crée. Dans le cas contraire, elle ouvre la clé. `CreateKey` définit ensuite `m_hKey` sur la clé créée ou ouverte.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a> CSettingsStore :: CSettingsStore

Crée un objet `CSettngsStore`.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Paramètres

*bAdmin*<br/>
dans Paramètre booléen qui spécifie si l' `CSettingsStore` objet agit en mode administrateur.

*bReadOnly*<br/>
dans Paramètre booléen qui spécifie si l' `CSettingsStore` objet est créé en mode lecture seule.

### <a name="remarks"></a>Notes

Si *bAdmin* a la valeur true, la `m_hKey` variable membre est définie sur **HKEY_LOCAL_MACHINE**. Si vous affectez à *bAdmin* la valeur false, `m_hKey` a la valeur **HKEY_CURRENT_USER**.

L’accès à la sécurité dépend du paramètre *bReadOnly* . Si *bReadonly* a la valeur false, l’accès à la sécurité est défini sur **KEY_ALL_ACCESS**. Si *bReadyOnly* a la valeur true, l’accès à la sécurité est défini sur une combinaison de **KEY_QUERY_VALUE, KEY_NOTIFY** et **KEY_ENUMERATE_SUB_KEYS**. Pour plus d’informations sur l’accès à la sécurité avec le registre, consultez [sécurité des clés de Registre et droits d’accès](/windows/win32/SysInfo/registry-key-security-and-access-rights).

Destructeur des mises en `CSettingsStore` production `m_hKey` automatiquement.

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a> CSettingsStore ::D eleteKey

Supprime une clé et tous ses enfants du Registre.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>Paramètres

*pszPath*<br/>
dans Nom de la clé à supprimer.

*bAdmin*<br/>
dans Commutateur qui spécifie l’emplacement de la clé à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode échoue si l' `CSettingsStore` objet est en mode lecture seule.

Si le paramètre *bAdmin* est égal à zéro, `DeleteKey` recherche la clé à supprimer sous **HKEY_CURRENT_USER**. Si *bAdmin* est différent de zéro, `DeleteKey` recherche la clé à supprimer sous **HKEY_LOCAL_MACHINE**.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a> CSettingsStore ::D eleteValue

Supprime une valeur de `m_hKey` .

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>Paramètres

*pszValue*<br/>
dans Spécifie le champ de valeur à supprimer.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="csettingsstoreopen"></a><a name="open"></a> CSettingsStore :: Open

Ouvre une clé de registre.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>Paramètres

*pszPath*<br/>
dans Nom d’une clé de registre.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Une fois que cette méthode a ouvert la clé spécifiée, elle définit `m_hKey` sur le handle de cette clé.

## <a name="csettingsstoreread"></a><a name="read"></a> CSettingsStore :: lecture

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

*pszKey*<br/>
dans Pointeur vers une chaîne se terminant par un caractère null qui contient le nom de la valeur à lire à partir du Registre.

*iVal*<br/>
à Référence à une variable de type entier qui reçoit la valeur lue à partir de la clé de registre.

*dwVal*<br/>
à Référence à une variable de mot double 32 bits qui reçoit la valeur lue à partir de la clé de registre.

*sVal*<br/>
à Référence à une variable de chaîne qui reçoit la valeur lue à partir de la clé de registre.

*scStringList*<br/>
à Référence à une variable de liste de chaînes qui reçoit la valeur lue à partir de la clé de registre.

*scArray*<br/>
à Référence à une variable de tableau de chaînes qui reçoit la valeur lue à partir de la clé de registre.

*dwcArray*<br/>
à Référence à une variable de tableau de mots doubles 32 bits qui reçoit la valeur lue à partir de la clé de registre.

*wcArray*<br/>
à Référence à une variable de tableau de mots 16 bits qui reçoit la valeur lue à partir de la clé de registre.

*bcArray*<br/>
à Référence à une variable de tableau d’octets qui reçoit la valeur lue à partir de la clé de registre.

*lpPoint*<br/>
à Référence à un pointeur vers une `POINT` structure qui reçoit la valeur lue à partir de la clé de registre.

*rectangulaire*<br/>
à Référence à une variable [CRect](../../atl-mfc-shared/reference/crect-class.md) qui reçoit la valeur lue à partir de la clé de registre.

*ppData*<br/>
à Pointeur vers un pointeur vers des données qui reçoit la valeur lue à partir de la clé de registre.

*pBytes*<br/>
à Pointeur vers une variable de type entier non signé. Cette variable reçoit la taille de la mémoire tampon vers laquelle pointe *ppData* .

*list*<br/>
à Référence à une variable [CObList](../../mfc/reference/coblist-class.md) qui reçoit la valeur lue à partir de la clé de registre.

*obj*<br/>
à Référence à une variable [CObject](../../mfc/reference/cobject-class.md) qui reçoit la valeur lue à partir de la clé de registre.

*pObj*<br/>
à Référence à un pointeur vers une `CObject` variable qui reçoit la valeur lue à partir de la clé de registre.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

`Read` recherche *pszKey* comme sous-clé de `m_hKey` .

## <a name="csettingsstorewrite"></a><a name="write"></a> CSettingsStore :: Write

Écrit une valeur dans le Registre sous la clé ouverte.

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

*pszKey*<br/>
dans Pointeur vers une chaîne qui contient le nom de la valeur à définir.

*iVal*<br/>
dans Référence à une variable de type entier qui contient les données à stocker.

*dwVal*<br/>
dans Référence à une variable de mot double 32 bits qui contient les données à stocker.

*pszVal*<br/>
dans Pointeur vers une variable de chaîne terminée par le caractère null qui contient les données à stocker.

*scStringList*<br/>
dans Référence à une variable [CStringList](../../mfc/reference/cstringlist-class.md) qui contient les données à stocker.

*bcArray*<br/>
dans Référence à une variable de tableau d’octets qui contient les données à stocker.

*scArray*<br/>
dans Référence à une variable de tableau de chaînes qui contient les données à stocker.

*dwcArray*<br/>
dans Référence à une variable de tableau de mots doubles 32 bits qui contient les données à stocker.

*wcArray*<br/>
dans Référence à une variable de tableau de mots 16 bits qui contient les données à stocker.

*rectangulaire*<br/>
dans Référence à une variable [CRect](../../atl-mfc-shared/reference/crect-class.md) qui contient les données à stocker.

*lpPoint*<br/>
dans Référence à un pointeur vers une `POINT` variable qui contient les données à stocker.

*pData*<br/>
dans Pointeur vers une mémoire tampon qui contient les données à stocker.

*nBytes*<br/>
dans Spécifie la taille, en octets, des données auxquelles le paramètre *pData* pointe.

*list*<br/>
dans Référence à une variable [CObList](../../mfc/reference/coblist-class.md) qui contient les données à stocker.

*obj*<br/>
dans Référence à une variable [CObject](../../mfc/reference/cobject-class.md) qui contient les données à stocker.

*pObj*<br/>
dans Pointeur vers un pointeur vers une `CObject` variable qui contient les données à stocker.

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

Pour écrire dans le registre, vous devez définir *bReadOnly* sur une valeur différente de zéro lorsque vous créez un objet [CSettingsStore](../../mfc/reference/csettingsstore-class.md) . Pour plus d’informations, consultez [CSettingsStore :: CSettingsStore](#csettingsstore).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx, classe](../../mfc/reference/cwinappex-class.md)

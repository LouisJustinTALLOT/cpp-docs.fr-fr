---
description: 'En savoir plus sur : classe CSettingsStoreSP'
title: CSettingsStoreSP, classe
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 67e9f881fc43722ab568aa7f149fc7a2b44cc764
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264685"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP, classe

La `CSettingsStoreSP` classe est une classe d’assistance que vous pouvez utiliser pour créer des instances de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

## <a name="syntax"></a>Syntaxe

```
class CSettingsStoreSP
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Construit un objet `CSettingsStoreSP`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CSettingsStoreSP :: Create](#create)|Crée une instance d’une classe dérivée de `CSettingsStore` .|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Définit la classe d’exécution. La `Create` méthode utilise la classe Runtime pour déterminer la classe d’objets à créer.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|`m_dwUserData`|Données utilisateur personnalisées qui sont stockées dans l' `CSettingsStoreSP` objet. Vous fournissez ces données dans le constructeur de l' `CSettingsStoreSP` objet.|
|`m_pRegistry`|`CSettingsStore`Objet dérivé de créé par la `Create` méthode.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser la `CSettingsStoreSP` classe pour rediriger toutes les opérations de Registre MFC vers d’autres emplacements, tels qu’un fichier XML ou une base de données. Pour ce faire, effectuez les étapes suivantes :

1. Créez une classe (telle que `CMyStore` ) et dérivez-la de `CSettingsStore` .

1. Utilisez [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) et des macros [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) avec votre `CSettingsStore` classe personnalisée pour activer la création dynamique.

1. Substituez les fonctions virtuelles et implémentez les `Read` `Write` fonctions et dans votre classe personnalisée. Implémentez toutes les autres fonctionnalités pour lire et écrire des données à l’emplacement souhaité.

1. Dans votre application, appelez `CSettingsStoreSP::SetRuntimeClass` et transmettez un pointeur vers la [structure CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obtenue à partir de votre classe.

Chaque fois que l’infrastructure accède généralement au registre, elle instancie désormais dynamiquement votre classe personnalisée et l’utilise pour lire ou écrire des données.

`CSettingsStoreSP::SetRuntimeClass` utilise une variable statique globale. Par conséquent, un seul magasin personnalisé est disponible à la fois.

## <a name="requirements"></a>Spécifications

**En-tête :** afxsettingsstore. h

## <a name="csettingsstorespcreate"></a><a name="create"></a> CSettingsStoreSP :: Create

Crée une nouvelle instance d’un objet dérivé de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Paramètres

*bAdmin*<br/>
dans Paramètre booléen qui détermine si un `CSettingsStore` objet est créé en mode administrateur.

*bReadOnly*<br/>
dans Paramètre booléen qui détermine si un `CSettingsStore` objet est créé pour un accès en lecture seule.

### <a name="return-value"></a>Valeur renvoyée

Référence à l’objet nouvellement créé `CSettingsStore` .

### <a name="remarks"></a>Notes

Vous pouvez utiliser la méthode [CSettingsStoreSP :: SetRuntimeClass](#setruntimeclass) pour déterminer le type d’objet qui `CSettingsStoreSP::Create` sera créé. Par défaut, cette méthode crée un `CSettingsStore` objet.

Si vous créez un `CSettingsStore` objet en mode administrateur, l’emplacement par défaut de tous les accès au registre est HKEY_LOCAL_MACHINE. Dans le cas contraire, l’emplacement par défaut de tous les accès au registre est HKEY_CURRENT_USER.

Si *bAdmin* a la valeur true, l’application doit disposer des droits d’administration. Dans le cas contraire, elle échouera lorsqu’elle tentera d’accéder au registre.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `Create` méthode de la `CSettingsStoreSP` classe.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a> CSettingsStoreSP::CSettingsStoreSP

Construit un objet de [classe CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) .

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*dwUserData*<br/>
dans Données définies par l’utilisateur stockées par l' `CSettingsStoreSP` objet.

### <a name="remarks"></a>Notes

L' `CSettingsStoreSP` objet stocke les données de *dwUserData* dans la variable membre protégée `m_dwUserData` .

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a> CSettingsStoreSP::SetRuntimeClass

Définit la classe d’exécution. La méthode [CSettingsStoreSP :: Create](#create) utilise la classe Runtime pour déterminer le type d’objet à créer.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Paramètres

*pRTI*<br/>
dans Pointeur vers les informations de classe Runtime pour une classe dérivée de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Valeur renvoyée

TRUE en cas de réussite ; FALSe si la classe identifiée par *PRTI* n’est pas dérivée de `CSettingsStore` .

### <a name="remarks"></a>Notes

Vous pouvez utiliser la [classe CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) pour dériver des classes de `CSettingsStore` . Utilisez la méthode `SetRuntimeClass` si vous souhaitez créer des objets d’une classe personnalisée dérivée de `CSettingsStore` .

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore, classe](../../mfc/reference/csettingsstore-class.md)

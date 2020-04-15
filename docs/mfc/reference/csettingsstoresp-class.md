---
title: Classe CSettingsStoreSP
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
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318451"
---
# <a name="csettingsstoresp-class"></a>Classe CSettingsStoreSP

La `CSettingsStoreSP` classe est une classe d’aide que vous pouvez utiliser pour créer des instances de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

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
|[CSettingsStoreSP::Créer](#create)|Crée une instance d’une `CSettingsStore`classe qui est dérivée de .|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Définit la classe de temps d’exécution. La `Create` méthode utilise la classe de temps d’exécution pour déterminer quelle classe d’objets créer.|

### <a name="data-members"></a>Données membres

|Nom|Description|
|----------|-----------------|
|`m_dwUserData`|Données utilisateur personnalisées stockées dans l’objet. `CSettingsStoreSP` Vous fournissez ces données dans `CSettingsStoreSP` le constructeur de l’objet.|
|`m_pRegistry`|L’objet `CSettingsStore`dérivé `Create` que la méthode crée.|

## <a name="remarks"></a>Notes

Vous pouvez `CSettingsStoreSP` utiliser la classe pour rediriger toutes les opérations de registre MFC vers d’autres endroits, comme un fichier XML ou une base de données. Pour ce faire, procédez comme suit :

1. Créez une classe `CMyStore`(comme ) `CSettingsStore`et dérivez-la de .

1. Utilisez [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) et [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) macros avec votre `CSettingsStore` classe personnalisée pour permettre une création dynamique.

1. Remplacez les fonctions virtuelles et implémentez les `Read` fonctions et `Write` les fonctions de votre classe personnalisée. Implémentez toute autre fonctionnalité pour lire et écrire des données à votre emplacement désiré.

1. Dans votre demande, appelez `CSettingsStoreSP::SetRuntimeClass` et passez un pointeur à la structure [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obtenue de votre classe.

Chaque fois que le cadre accède généralement au registre, il instantanémenta désormais dynamiquement votre classe personnalisée et l’utilisera pour lire ou écrire des données.

`CSettingsStoreSP::SetRuntimeClass`utilise une variable statique globale. Par conséquent, un seul magasin personnalisé est disponible à la fois.

## <a name="requirements"></a>Spécifications

**En-tête:** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP::Créer

Crée une nouvelle instance d’un objet qui est dérivé de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Paramètres

*bAdmin (en)*<br/>
[dans] Un paramètre Boolean qui `CSettingsStore` détermine si un objet est créé en mode administrateur.

*bReadOnly*<br/>
[dans] Un paramètre Boolean qui `CSettingsStore` détermine si un objet est créé pour un accès sans lecture seulement.

### <a name="return-value"></a>Valeur de retour

Une référence à `CSettingsStore` l’objet nouvellement créé.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la méthode [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) `CSettingsStoreSP::Create` pour déterminer quel type d’objet va créer. Par défaut, cette `CSettingsStore` méthode crée un objet.

Si vous `CSettingsStore` créez un objet en mode administrateur, l’emplacement par défaut pour tous les accès au registre est HKEY_LOCAL_MACHINE. Dans le cas contraire, l’emplacement par défaut pour tous les accès au registre est HKEY_CURRENT_USER.

Si *bAdmin* est VRAI, la demande doit avoir des droits d’administration. Sinon, il échouera quand il essaie d’accéder au registre.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `Create` utiliser `CSettingsStoreSP` la méthode de la classe.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP

Construit un objet [de classe CSettingsStoreSP.](../../mfc/reference/csettingsstoresp-class.md)

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*dwUserData*<br/>
[dans] Données définies par `CSettingsStoreSP` l’utilisateur que l’objet stocke.

### <a name="remarks"></a>Notes

L’objet `CSettingsStoreSP` stocke les données de *dwUserData* dans la variable `m_dwUserData`protégée des membres.

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass

Définit la classe de temps d’exécution. La méthode [CSettingsStoreSP::Create](#create) utilise la classe de temps d’exécution pour déterminer quel type d’objet créer.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Paramètres

*pRTI (en)*<br/>
[dans] Un pointeur à l’information de classe de temps d’exécution pour une classe dérivée de la [classe CSettingsStore](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Valeur de retour

VRAI en cas de succès; FALSE si la classe identifiée par *pRTI* n’est pas dérivée de `CSettingsStore`.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la [classe CSettingsStoreSP](../../mfc/reference/csettingsstoresp-class.md) pour tirer des classes de `CSettingsStore`. Utilisez la `SetRuntimeClass` méthode si vous voulez créer des objets `CSettingsStore`d’une classe personnalisée qui est dérivé de .

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore, classe](../../mfc/reference/csettingsstore-class.md)

---
title: Csettingsstoresp, classe
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
ms.openlocfilehash: 5c7a992b983552340ebe21e59d2ee9a667841ec0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275192"
---
# <a name="csettingsstoresp-class"></a>Csettingsstoresp, classe

Le `CSettingsStoreSP` classe est une classe d’assistance que vous pouvez utiliser pour créer des instances de la [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md).

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
|[CSettingsStoreSP::Create](#create)|Crée une instance d’une classe dérivée de `CSettingsStore`.|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Définit la classe d’exécution. Le `Create` méthode utilise la classe d’exécution pour déterminer quelle classe d’objets à créer.|

### <a name="data-members"></a>Membres de données

|Name|Description|
|----------|-----------------|
|`m_dwUserData`|Les données utilisateur personnalisées qui sont stockées dans le `CSettingsStoreSP` objet. Vous fournissez ces données dans le constructeur de la `CSettingsStoreSP` objet.|
|`m_pRegistry`|Le `CSettingsStore`-dérivée de l’objet qui le `Create` crée de la méthode.|

## <a name="remarks"></a>Notes

Vous pouvez utiliser la `CSettingsStoreSP` classe pour rediriger toutes les opérations de Registre MFC à d’autres emplacements, par exemple un fichier XML ou une base de données. Pour ce faire, procédez comme suit :

1. Créer une classe (tel que `CMyStore`) et dérivez-le de `CSettingsStore`.

1. Utilisez [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) et [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) macros avec votre personnalisé `CSettingsStore` classe pour permettre la création dynamique.

1. Remplacer les fonctions virtuelles et implémenter la `Read` et `Write` fonctions dans votre classe personnalisée. Implémenter d’autres fonctionnalités pour lire et écrire des données à l’endroit souhaité.

1. Dans votre application, appelez `CSettingsStoreSP::SetRuntimeClass` et passez un pointeur vers le [CRuntimeClass, Structure](../../mfc/reference/cruntimeclass-structure.md) obtenu à partir de votre classe.

Chaque fois que l’infrastructure accéderait généralement le Registre, il va maintenant dynamiquement instancier votre classe personnalisée et l’utiliser pour lire ou écrire des données.

`CSettingsStoreSP::SetRuntimeClass` utilise une variable statique globale. Par conséquent, qu’un seul magasin personnalisé est disponible à la fois.

## <a name="requirements"></a>Spécifications

**En-tête :** afxsettingsstore.h

##  <a name="create"></a>  CSettingsStoreSP::Create

Crée une nouvelle instance d’un objet qui est dérivé le [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md).

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Paramètres

*bAdmin*<br/>
[in] Un paramètre booléen qui détermine si un `CSettingsStore` objet est créé en mode administrateur.

*bReadOnly*<br/>
[in] Un paramètre booléen qui détermine si un `CSettingsStore` objet est créé pour l’accès en lecture seule.

### <a name="return-value"></a>Valeur de retour

Une référence à ce nouveau `CSettingsStore` objet.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la méthode [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) pour déterminer le type d’objet `CSettingsStoreSP::Create` va créer. Par défaut, cette méthode crée un `CSettingsStore` objet.

Si vous créez un `CSettingsStore` objet en mode administrateur, l’emplacement par défaut pour tous les accès de Registre HKEY_LOCAL_MACHINE. Sinon, l’emplacement par défaut pour tous les accès de Registre est HKEY_CURRENT_USER.

Si *bCheminAdmin* a la valeur TRUE, l’application doit avoir des droits d’administration. Sinon, il risque d’échouer lorsqu’il tente d’accéder au Registre.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le `Create` méthode de la `CSettingsStoreSP` classe.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

##  <a name="csettingsstoresp"></a>  CSettingsStoreSP::CSettingsStoreSP

Construit un [csettingsstoresp, classe](../../mfc/reference/csettingsstoresp-class.md) objet.

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Paramètres

*dwUserData*<br/>
[in] Données définies par l’utilisateur qui le `CSettingsStoreSP` stocke l’objet.

### <a name="remarks"></a>Notes

Le `CSettingsStoreSP` objet stocke les données à partir de *dwUserData* dans la variable membre protégé `m_dwUserData`.

##  <a name="setruntimeclass"></a>  CSettingsStoreSP::SetRuntimeClass

Définit la classe d’exécution. La méthode [CSettingsStoreSP::Create](#create) utilise la classe d’exécution pour déterminer le type d’objet à créer.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Paramètres

*pRTI*<br/>
[in] Un pointeur vers les informations de classe runtime pour une classe dérivée de la [CSettingsStore Class](../../mfc/reference/csettingsstore-class.md).

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite ; FALSE si la classe identifiée par *pRTI* n’est pas dérivé `CSettingsStore`.

### <a name="remarks"></a>Notes

Vous pouvez utiliser la [csettingsstoresp, classe](../../mfc/reference/csettingsstoresp-class.md) de dériver des classes à partir de `CSettingsStore`. Utilisez la méthode `SetRuntimeClass` si vous souhaitez créer des objets d’une classe personnalisée dérivée de `CSettingsStore`.

## <a name="see-also"></a>Voir aussi

[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore, classe](../../mfc/reference/csettingsstore-class.md)

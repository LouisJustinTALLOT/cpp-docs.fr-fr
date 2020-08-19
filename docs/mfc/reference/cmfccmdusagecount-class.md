---
title: CMFCCmdUsageCount, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: 15026746f2af55b9cc153cce19cf00475e5c5d77
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561100"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount, classe

Effectue le suivi du nombre d’utilisations des messages Windows, par exemple lorsque l’utilisateur sélectionne un élément dans un menu.

## <a name="syntax"></a>Syntaxe

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Constructeur par défaut.|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Incrémente d’une unité le compteur associé à la commande donnée.|
|[CMFCCmdUsageCount :: GetCount](#getcount)|Récupère le nombre d’utilisations associées à l’ID de commande donné.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Détermine si cet objet a collecté la quantité minimale de données de suivi.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Détermine si la commande donnée est fréquemment utilisée.|
|[CMFCCmdUsageCount :: Reset](#reset)|Efface le nombre d’utilisations de toutes les commandes.|
|[CMFCCmdUsageCount :: Serialize](#serialize)|Lit cet objet à partir d’une archive ou l’écrit dans une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Définit les valeurs des `CMFCCmdUsageCount` membres de données de classe partagée.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|`m_CmdUsage`|`CMap`Objet qui mappe des commandes à leur nombre d’utilisations.|
|`m_nMinUsagePercentage`|Pourcentage d’utilisation minimal pour une commande à utiliser fréquemment.|
|`m_nStartCount`|Le compteur de démarrage utilisé pour déterminer si cet objet a collecté la quantité minimale de données de suivi.|
|`m_nTotalUsage`|Nombre total de commandes suivies.|

### <a name="remarks"></a>Notes

La `CMFCCmdUsageCount` classe mappe chaque identificateur de message Windows numérique à un compteur d’entiers non signés 32 bits. `CMFCToolBar` utilise cette classe pour afficher des éléments de barre d’outils fréquemment utilisés. Pour plus d’informations sur `CMFCToolBar` , consultez [CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md).

Vous pouvez conserver `CMFCCmdUsageCount` les données de classe entre les exécutions de votre programme. Utilisez la méthode [CMFCCmdUsageCount :: Serialize](#serialize) pour sérialiser des données de membre de classe et la méthode [CMFCCmdUsageCount :: SetOptions](#setoptions) pour définir des données de membre partagé.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmdusagecount. h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a> CMFCCmdUsageCount::AddCmd

Incrémente d’une unité le compteur associé à la commande donnée.

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*\
dans Spécifie le compteur de commandes à incrémenter.

### <a name="remarks"></a>Notes

Cette méthode ajoute une nouvelle entrée à la structure de la carte du nombre de commandes, `m_CmdUsage` , si l’entrée n’existe pas encore.

Cette méthode n’a aucun effet dans les cas suivants :

- L’infrastructure de barre d’outils est en mode de personnalisation (la méthode [CMFCToolBar :: IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) retourne une valeur différente de zéro).

- La commande fait référence à un sous-menu ou à un séparateur de menu ( *uiCmd* est égal à 0 ou-1).

- *uiCmd* fait référence à une commande standard (la `IsStandardCommand` fonction globale retourne une valeur différente de zéro).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a> CMFCCmdUsageCount :: GetCount

Récupère le nombre d’utilisations associées à l’ID de commande donné.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Paramètres

*uiCmd*\
dans ID du compteur de commandes à récupérer.

### <a name="return-value"></a>Valeur de retour

Nombre d’utilisations associées à l’ID de commande donné.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a> CMFCCmdUsageCount::HasEnoughInformation

Détermine si cet objet a reçu la quantité minimale de données de suivi.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si cet objet a reçu la quantité minimale de données de suivi ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode retourne une valeur différente de zéro si le nombre total, `m_nTotalUsage` , de toutes les commandes suivies est égal ou supérieur au nombre initial, `m_nStartCount` . Par défaut, l’infrastructure définit le nombre initial 0. Vous pouvez remplacer cette valeur à l’aide de la méthode [CMFCCmdUsageCount :: SetOptions](#setoptions) .

Cette méthode est utilisée par [CMFCMenuBar :: IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) pour déterminer s’il faut afficher toutes les commandes de menu disponibles.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a> CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Détermine si la commande donnée est fréquemment utilisée.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Paramètres

*uiCmd*\
dans Spécifie la commande à vérifier.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la commande est fréquemment utilisée ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode retourne 0 si l’utilisation totale de la commande, `m_nTotalUsage` , est 0. Sinon, cette méthode retourne une valeur différente de zéro si le pourcentage d’utilisation de la commande spécifiée est supérieur au pourcentage minimal, `m_nMinUsagePercentage` . Par défaut, l’infrastructure définit le pourcentage minimal sur 5. Vous pouvez remplacer cette valeur à l’aide de la méthode [CMFCCmdUsageCount :: SetOptions](#setoptions) . Si le pourcentage minimal est 0, cette méthode retourne une valeur différente de zéro si le nombre de commandes spécifié est supérieur à 0.

[CMFCToolBar :: IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) utilise cette méthode pour déterminer si une commande est rarement utilisée.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a> CMFCCmdUsageCount :: Reset

Efface le nombre d’utilisations de toutes les commandes.

```cpp
void Reset();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour effacer toutes les entrées de la structure cartographique des nombres de commandes, `m_CmdUsage` et pour réinitialiser l’utilisation totale de la commande, `m_nTotalUsage` , Counter à 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a> CMFCCmdUsageCount :: Serialize

Lit cet objet à partir d’une archive ou l’écrit dans une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*AR*\
dans `CArchive` Objet à sérialiser à partir de ou vers.

### <a name="remarks"></a>Notes

Cette méthode sérialise la structure de la carte des nombres de commandes, `m_CmdUsage` et l’utilisation totale des commandes, `m_nTotalUsage` , le compteur à partir de ou vers l’archive spécifiée.

Pour obtenir des exemples de sérialisation, consultez [sérialisation : sérialisation d’un objet](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a> CMFCCmdUsageCount::SetOptions

Définit les valeurs des `CMFCCmdUsageCount` membres de données de classe partagée.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Paramètres

*nStartCount*\
dans Nouveau nombre initial de toutes les commandes suivies.

*nMinUsagePercentage*\
dans Nouveau pourcentage d’utilisation minimal.

### <a name="return-value"></a>Valeur de retour

TRUE si la méthode a la valeur FALSe si le paramètre *nMinUsagePercentage* est supérieur ou égal à 100.

### <a name="remarks"></a>Notes

Cette méthode définit les `CMFCCmdUsageCount` membres de données de classe partagée `m_nStartCount` et `m_nMinUsagePercentage` sur *nStartCount* et *nMinUsagePercentage*, respectivement. `m_nStartCount` est utilisé par la méthode [CMFCCmdUsageCount :: HasEnoughInformation](#hasenoughinformation) pour déterminer si cet objet a collecté la quantité minimale de données de suivi. `m_nMinUsagePercentage` est utilisé par la méthode [CMFCCmdUsageCount :: IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) pour déterminer si une commande donnée est fréquemment utilisée.

Dans les versions Debug, cette méthode génère un échec d’assertion si le paramètre *nMinUsagePercentage* est supérieur ou égal à 100.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)

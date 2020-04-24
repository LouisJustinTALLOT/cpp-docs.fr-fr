---
title: Classe CMFCCmdUsageCount
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
ms.openlocfilehash: 02b302ec38922128190a6f20ce2f156b52383b55
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752581"
---
# <a name="cmfccmdusagecount-class"></a>Classe CMFCCmdUsageCount

Suit le nombre d’utilisations des messages Windows, par exemple lorsque l’utilisateur sélectionne un élément à partir d’un menu.

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
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Incréments par un le compteur qui est associé à la commande donnée.|
|[CMFCCmdUsageCount::GetCount](#getcount)|Récupère le nombre d’utilisations qui est associé à l’ID de commande donné.|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Détermine si cet objet a recueilli la quantité minimale de données de suivi.|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Détermine si la commande donnée est fréquemment utilisée.|
|[CMFCCmdUsageCount::Reset](#reset)|Efface le nombre d’utilisation de toutes les commandes.|
|[CMFCCmdUsageCount::Serialize](#serialize)|Lit cet objet à partir d’une archive ou l’écrit à une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Définit les valeurs `CMFCCmdUsageCount` des membres de données de classe partagées.|

### <a name="data-members"></a>Données membres

|||
|-|-|
|Nom|Description|
|`m_CmdUsage`|Un `CMap` objet qui cartographie les commandes à leur utilisation compte.|
|`m_nMinUsagePercentage`|Le pourcentage d’utilisation minimum pour une commande à utiliser fréquemment.|
|`m_nStartCount`|Le compteur de démarrage qui est utilisé pour déterminer si cet objet a recueilli la quantité minimale de données de suivi.|
|`m_nTotalUsage`|Le décompte de toutes les commandes suivies.|

### <a name="remarks"></a>Notes

La `CMFCCmdUsageCount` classe cartographie chaque identifiant numérique de message Windows à un compteur integer non signé 32 bits. `CMFCToolBar`utilise cette classe pour afficher des éléments de barre d’outils fréquemment utilisés. Pour plus `CMFCToolBar`d’informations sur , voir [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).

Vous pouvez `CMFCCmdUsageCount` persévérer les données de classe entre les exécutions de votre programme. Utilisez la méthode [CMFCCmdUsageCount::Serialize](#serialize) pour sérialiser les données des membres de la classe et la méthode [CMFCCmdUsageCount::SetOptions](#setoptions) pour définir les données partagées des membres.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCompte](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxcmdusagecount.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmdUsageCount::AddCmd

Incréments par un le compteur qui est associé à la commande donnée.

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*uiCmd uiCmd*|[dans] Spécifie le compteur de commande à l’incrément.|

### <a name="remarks"></a>Notes

Cette méthode ajoute une nouvelle entrée à `m_CmdUsage`la structure de la carte des comptes de commande, si l’entrée n’existe pas déjà.

Cette méthode ne fait rien dans les cas suivants :

- Le cadre de la barre d’outils est en mode personnalisation (le [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) méthode retourne une valeur non zéro).

- La commande se réfère à un sous-mois ou un séparateur de menu *(uiCmd* égal à 0 ou -1).

- *uiCmd* se réfère à une `IsStandardCommand` commande standard (la fonction globale retourne une valeur non zéro).

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmdUsageCount::GetCount

Récupère le nombre d’utilisations qui est associé à l’ID de commande donné.

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*uiCmd uiCmd*|[dans] L’ID du compteur de commande à récupérer.|

### <a name="return-value"></a>Valeur de retour

Le nombre d’utilisation qui est associé à l’ID de commande donné.

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation

Détermine si cet objet a reçu la quantité minimale de données de suivi.

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si cet objet a reçu la quantité minimale de données de suivi; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode renvoie une valeur non `m_nTotalUsage`zéro si le nombre total, , de toutes `m_nStartCount`les commandes suivies est égale ou supérieure au nombre initial, . Par défaut, le cadre définit le décompte initial 0. Vous pouvez remplacer cette valeur en utilisant la méthode [CMFCCmdUsageCount::SetOptions.](#setoptions)

Cette méthode est utilisée par [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) pour déterminer s’il convient d’afficher toutes les commandes de menu disponibles.

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

Détermine si la commande donnée est fréquemment utilisée.

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*uiCmd uiCmd*|[dans] Spécifie l’ordre de vérifier.|

### <a name="return-value"></a>Valeur de retour

Nonzero si la commande est fréquemment utilisée; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode renvoie 0 si `m_nTotalUsage`l’utilisation totale de commande, , est de 0. Dans le cas contraire, cette méthode renvoie nonzero si le pourcentage `m_nMinUsagePercentage`de laquelle la commande spécifiée est utilisée est plus grand que le pourcentage minimum, . Par défaut, le cadre fixe le pourcentage minimum à 5. Vous pouvez remplacer cette valeur en utilisant la méthode [CMFCCmdUsageCount::SetOptions.](#setoptions) Si le pourcentage minimum est de 0, cette méthode renvoie nonzero si le nombre de commandes spécifié est supérieur à 0.

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) utilise cette méthode pour déterminer si une commande est rarement utilisée.

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmdUsageCount::Reset

Efface le nombre d’utilisation de toutes les commandes.

```cpp
void Reset();
```

### <a name="remarks"></a>Notes

Appelez cette méthode pour effacer toutes les entrées `m_CmdUsage`de la structure de `m_nTotalUsage`la carte des comptes de commande, et pour réinitialiser l’utilisation totale de commande, , contre 0.

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmdUsageCount::Serialize

Lit cet objet à partir d’une archive, ou l’écrit à une archive.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*Ar*|[dans] Un `CArchive` objet à sérialiser de ou vers.|

### <a name="remarks"></a>Notes

Cette méthode sérialise la structure `m_CmdUsage`cartographique des comptes `m_nTotalUsage`de commande, et l’utilisation totale de commande, , contre ou à l’archive spécifiée.

Pour des exemples de sérialisation, voir [Serialization: Serializing an Object](../../mfc/serialization-serializing-an-object.md).

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmdUsageCount::SetOptions

Définit les valeurs `CMFCCmdUsageCount` des membres de données de classe partagées.

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>Paramètres

|||
|-|-|
|Paramètre|Description|
|*nStartCount (en)*|[dans] Le nouveau décompte initial de toutes les commandes suivies.|
|*nMinUsagePercentage (en)*|[dans] Le nouveau pourcentage d’utilisation minimum.|

### <a name="return-value"></a>Valeur de retour

VRAI si la méthode réussit, FALSE si le *paramètre nMinUsagePercentage* est plus grand ou égal à 100.

### <a name="remarks"></a>Notes

Cette méthode définit `CMFCCmdUsageCount` les `m_nStartCount` membres `m_nMinUsagePercentage` des données de classe partagées et à *nStartCount* et *nMinUsagePercentage*, respectivement. `m_nStartCount`est utilisé par le [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) méthode pour déterminer si cet objet a recueilli la quantité minimale de données de suivi. `m_nMinUsagePercentage`est utilisé par le [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) méthode pour déterminer si une commande donnée est fréquemment utilisé.

Dans Debug construit cette méthode génère une défaillance d’affirmation si le paramètre *nMinUsagePercentage* est plus grand ou égal à 100.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
